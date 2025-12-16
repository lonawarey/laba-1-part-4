#include <stdio.h>
#include <stdlib.h>

int main() {
    FILE *file;
    char filename[100];
    double number, sum = 0.0;
    int position = 0;
    
    printf("Введите имя файла: ");
    scanf("%s", filename);
    
    file = fopen(filename, "r");
    if (file == NULL) {
        printf("Ошибка открытия файла\n");
        return 1;
    }
    
    printf("Чтение файла '%s':\n", filename);
    
    while (fscanf(file, "%lf", &number) == 1) {
        position++;
        
        if (position % 2 == 0) {
            sum += number;
            printf("Позиция %d (четная): %.2f\n", position, number);
        } else {
            printf("Позиция %d: %.2f\n", position, number);
        }
    }
    
    fclose(file);
    
    printf("\nИтого:\n");
    printf("Всего чисел: %d\n", position);
    printf("Сумма элементов на четных позициях: %.2f\n", sum);
    
    return 0;
}
