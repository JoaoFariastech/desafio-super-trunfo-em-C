[desafio.c](https://github.com/user-attachments/files/22732548/desafio.c)
#include <stdio.h>

int main() {
    // Carta 1
    char estado1;
    char codigoCarta1[10];
    char nomeCidade1[40];
    int populacao1;
    float area1;
    float PIB1;
    int NPM1; 
    float densidadePopulacional1;

    // Carta 2
    char estado2;
    char codigoCarta2[10];
    char nomeCidade2[40];
    int populacao2;
    float area2;
    float PIB2;
    int NPM2;
    float densidadePopulacional2;

    // Entrada Carta 1
    printf("=== Cadastro da Carta 1 ===\n");
    printf("Digite o estado da carta 1 (A-H): ");
    scanf(" %c", &estado1);

    printf("Digite o código da carta 1 (ex: A01): ");
    scanf("%9s", codigoCarta1);

    printf("Digite o nome do país/cidade da carta 1: ");
    scanf(" %39[^\n]", nomeCidade1);

    printf("Digite a população da carta 1: ");
    scanf("%d", &populacao1);

    printf("Digite a área da carta 1 (em km²): ");
    scanf("%f", &area1);

    printf("Digite o PIB da carta 1 (em bilhões): ");
    scanf("%f", &PIB1);

    printf("Digite o número de pontos turísticos da carta 1: ");
    scanf("%d", &NPM1);

    densidadePopulacional1 = populacao1 / area1;

    // Entrada Carta 2
    printf("\n=== Cadastro da Carta 2 ===\n");
    printf("Digite o estado da carta 2 (A-H): ");
    scanf(" %c", &estado2);

    printf("Digite o código da carta 2 (ex: B02): ");
    scanf("%9s", codigoCarta2);

    printf("Digite o nome do país/cidade da carta 2: ");
    scanf(" %39[^\n]", nomeCidade2);

    printf("Digite a população da carta 2: ");
    scanf("%d", &populacao2);

    printf("Digite a área da carta 2 (em km²): ");
    scanf("%f", &area2);

    printf("Digite o PIB da carta 2 (em bilhões): ");
    scanf("%f", &PIB2);

    printf("Digite o número de pontos turísticos da carta 2: ");
    scanf("%d", &NPM2);

    densidadePopulacional2 = populacao2 / area2;

    // Menu de atributos
    int opcao1, opcao2;
    printf("\n=== MENU DE ATRIBUTOS ===\n");
    printf("1 - População\n");
    printf("2 - Área\n");
    printf("3 - PIB\n");
    printf("4 - Número de Pontos Turísticos\n");
    printf("5 - Densidade Demográfica\n");

    // Primeiro atributo
    printf("Escolha o PRIMEIRO atributo: ");
    scanf("%d", &opcao1);

    // Segundo atributo (dinâmico)
    do {
        printf("Escolha o SEGUNDO atributo (diferente do primeiro): ");
        scanf("%d", &opcao2);
        if (opcao1 == opcao2) {
            printf("⚠ Você já escolheu esse atributo! Escolha outro.\n");
        }
    } while (opcao1 == opcao2);

    // Função auxiliar de comparação
    float valor1a, valor2a, valor1b, valor2b;
    float soma1 = 0, soma2 = 0;

    // Primeiro atributo
    switch (opcao1) {
        case 1: valor1a = populacao1; valor2a = populacao2; break;
        case 2: valor1a = area1; valor2a = area2; break;
        case 3: valor1a = PIB1; valor2a = PIB2; break;
        case 4: valor1a = NPM1; valor2a = NPM2; break;
        case 5: valor1a = densidadePopulacional1; valor2a = densidadePopulacional2; break;
    }

    // Segundo atributo
    switch (opcao2) {
        case 1: valor1b = populacao1; valor2b = populacao2; break;
        case 2: valor1b = area1; valor2b = area2; break;
        case 3: valor1b = PIB1; valor2b = PIB2; break;
        case 4: valor1b = NPM1; valor2b = NPM2; break;
        case 5: valor1b = densidadePopulacional1; valor2b = densidadePopulacional2; break;
    }

    // Comparação
    soma1 += (opcao1 == 5) ? (valor1a < valor2a) : (valor1a > valor2a);
    soma2 += (opcao1 == 5) ? (valor2a < valor1a) : (valor2a > valor1a);

    soma1 += (opcao2 == 5) ? (valor1b < valor2b) : (valor1b > valor2b);
    soma2 += (opcao2 == 5) ? (valor2b < valor1b) : (valor2b > valor1b);

    // Exibição do resultado
    printf("\n=== RESULTADO FINAL ===\n");
    printf("%s -> Soma de atributos: %.0f\n", nomeCidade1, soma1);
    printf("%s -> Soma de atributos: %.0f\n", nomeCidade2, soma2);

    if (soma1 > soma2) {
        printf("Vencedor: %s\n", nomeCidade1);
    } else if (soma2 > soma1) {
        printf("Vencedor: %s\n", nomeCidade2);
    } else {
        printf("Empate!\n");
    }

    return 0;
}
