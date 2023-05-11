#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_FILES 100
#define MAX_FILENAME_LENGTH 50

struct Directory {
    char filenames[MAX_FILES][MAX_FILENAME_LENGTH];
    int fileCount;
};

void initializeDirectory(struct Directory *dir) {
    dir->fileCount = 0;
}

void createFile(struct Directory *dir, const char *filename) {
    if (dir->fileCount >= MAX_FILES) {
        printf("Directory is full. Cannot create more files.\n");
        return;
    }

    strcpy(dir->filenames[dir->fileCount], filename);
    dir->fileCount++;
    printf("File '%s' created successfully.\n", filename);
}

void deleteFile(struct Directory *dir, const char *filename) {
    int i, fileIndex = -1;

    for (i = 0; i < dir->fileCount; i++) {
        if (strcmp(dir->filenames[i], filename) == 0) {
            fileIndex = i;
            break;
        }
    }

    if (fileIndex == -1) {
        printf("File '%s' not found.\n", filename);
        return;
    }

    for (i = fileIndex; i < dir->fileCount - 1; i++) {
        strcpy(dir->filenames[i], dir->filenames[i + 1]);
    }

    dir->fileCount--;
    printf("File '%s' deleted successfully.\n", filename);
}

void listFiles(struct Directory *dir) {
    int i;

    if (dir->fileCount == 0) {
        printf("No files found in the directory.\n");
        return;
    }

    printf("Files in the directory:\n");
    for (i = 0; i < dir->fileCount; i++) {
        printf("%s\n", dir->filenames[i]);
    }
}

int main() {
    struct Directory dir;
    initializeDirectory(&dir);

    int choice;
    char filename[MAX_FILENAME_LENGTH];

    while (1) {
        printf("\n--- Single-Level Directory System ---\n");
        printf("1. Create a file\n");
        printf("2. Delete a file\n");
        printf("3. List files\n");
        printf("4. Exit\n");
        printf("Enter your choice: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                printf("Enter the filename: ");
                scanf("%s", filename);
                createFile(&dir, filename);
                break;
            case 2:
                printf("Enter the filename: ");
                scanf("%s", filename);
                deleteFile(&dir, filename);
                break;
            case 3:
                listFiles(&dir);
                break;
            case 4:
                printf("Exiting the program.\n");
                exit(0);
            default:
                printf("Invalid choice. Please try again.\n");
        }
    }

    return 0;
}
