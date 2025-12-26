# Jogo-da-Velha-Aleatorizado
Implementação em C do resolvedor de Sudoku, ideal para estudantes de ensino médio e superior. Serve como exemplo prático de algoritmos (backtracking), estruturas de dados e modelagem matemática.

Resolvedor de Sudoku em C
Este projeto implementa um resolvedor automático de Sudoku usando algoritmo de backtracking. Ideal para estudantes de programação que desejam estudar:

Recursão e backtracking.

Estruturas de dados (matriz 9×9).

Modelagem matemática de restrições.

Como usar
Passo 1: Preparar o ambiente
Você precisa de um compilador C. Escolha uma opção:

IDE (recomendado para estudantes):

Code::Blocks (Windows/Linux)

VS Code + extensão C/C++

Dev‑C++ (Windows)

Terminal/Linha de comando:

Linux/macOS: gcc (instale via sudo apt install gcc se necessário).

Windows: MinGW ou WSL (Windows Subsystem for Linux).

Online (sem instalação):



Passo 2: Compilar e executar
Opção A: Via IDE (ex: Code::Blocks)
Abra o projeto no Code::Blocks.

Clique em Build (ou F9) para compilar.

Clique em Run (ou F10) para executar.

Opção B: Via terminal (Linux/macOS/WSL)
bash
gcc sudoku_solver.c -o sudoku
./sudoku
Opção C: Online (repl.it, etc.)
Cole o código no editor online.

Clique em Run (botão verde).

Passo 3: Inserir o tabuleiro
Ao executar, o programa pedirá que você digite 81 números (9 linhas × 9 colunas), onde:

1-9 = números fixos.

0 = casa vazia.

Exemplo de entrada (primeira linha):

5 3 0 0 7 0 0 0 0
Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência».

Nesse caso, eleI reinicia automaticamente com um tabuleiro padrão pré‑definido (não exibe mensagem).

O resolvedor então tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial

Números preenchidos.

. (pontos) para casas vazias.

Mensagem de processamento

Resolvendo...
Solução final (se existir)

Todos os . substituídos por números de 1 a 9.

Ou mensagem: "Não existe solução para este Sudoku."

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas.

Permita leitura de arquivo .txt.

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
"Sem solução"	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...

Resolvendo...

Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...

Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência». Nesse caso:

Reinicia automaticamente com um tabuleiro padrão pré‑definido (sem exibir mensagem);

Tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial:

Números preenchidos;

. (pontos) para casas vazias.

Mensagem de processamento:

Resolvendo...
Solução final (se existir):

Todos os . substituídos por números de 1 a 9;

Ou mensagem: «Não existe solução para este Sudoku.»

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas;

Permita leitura de arquivo .txt;

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
«Sem solução»	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...


Resolvendo...


Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...
Requisitos
Compilador C (gcc, clang ou equivalente);

Biblioteca padrão do C (stdio.h, stdbool.h);

Sistema operacional: Windows/Linux/macOS.

Exemplos de entrada/saída
Entrada válida (1 linha):
5 3 0 0 7 0 0 0 0

Entrada inválida (números fora de 0-9):
5 3 10 0 7 0 0 0 0 → causará erro

Funcionalidade «Bandeira Branca»
Se você digitar 0 em todas as 81 posições, o programa interpreta como «desistência». Nesse caso:

Reinicia automaticamente com um tabuleiro padrão pré‑definido (sem exibir mensagem);

Tenta solucionar o novo tabuleiro.

Nota: Esta funcionalidade permite recomeçar sem fechar o programa.

Passo 4: Entender a saída
Após a entrada, você verá:

Tabuleiro inicial:

Números preenchidos;

. (pontos) para casas vazias.

Mensagem de processamento:

Resolvendo...
Solução final (se existir):

Todos os . substituídos por números de 1 a 9;

Ou mensagem: «Não existe solução para este Sudoku.»

Passo 5: Modificar o tabuleiro padrão (opcional)
Se quiser alterar o tabuleiro que é carregado após a «bandeira branca», edite a matriz tabuleiroPadrao na função main:

c
int tabuleiroPadrao[N][N] = {
    {5, 3, 0, 0, 7, 0, 0, 0, 0},
    {6, 0, 0, 1, 9, 5, 0, 0, 0},
    // ... (adicione as 9 linhas)
};
Código-fonte: trechos chaves
1. Função para verificar tabuleiro vazio
c
bool tabuleiroVazio(int tabuleiro[N][N]) {
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            if (tabuleiro[i][j] != 0) {
                return false;
            }
        }
    }
    return true;
}
2. Lógica na main() (resumo)
c
int main() {
    int tabuleiro[N][N];
    
    // Lê 81 números do usuário
    for (int i = 0; i < N; i++) {
        for (int j = 0; j < N; j++) {
            scanf("%d", &tabuleiro[i][j]);
        }
    }
    
    // Se todos são 0 → reinicia com tabuleiro padrão
    if (tabuleiroVazio(tabuleiro)) {
        // Carrega tabuleiro pré‑definido
        for (int i = 0; i < N; i++) {
            for (int j = 0; j < N; j++) {
                tabuleiro[i][j] = tabuleiroPadrao[i][j];
            }
        }
    }
    
    // Continua com a resolução normal
    imprimirTabuleiro(tabuleiro);
    if (resolverSudoku(tabuleiro)) {
        printf("\nSolucao encontrada:\n");
        imprimirTabuleiro(tabuleiro);
    } else {
        printf("\nNao existe solucao para este Sudoku.\n");
    }
    
    return 0;
}
Dicas para estudantes
Analise resolverSudoku(): é um exemplo clássico de backtracking.

Teste casos extremos: tabuleiro vazio, solução impossível, tabuleiro completo.

Expanda o projeto:

Adicione contagem de tentativas;

Permita leitura de arquivo .txt;

Crie um modo interativo (jogador insere números passo a passo).

Problemas comuns e soluções
Problema	Solução
Erro de compilação	Verifique se todos os #include estão no código.
Não imprime nada	Confira se main() chama imprimirTabuleiro().
«Sem solução»	O tabuleiro pode ter números inválidos (repetições na linha/coluna).
Exemplo de saída
=== JOGO DE SUDOKU ===

Digite o tabuleiro (0 para casas vazias):
[Aqui você digita 9 linhas de 9 números]


Tabuleiro inicial:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 . | . 7 . | . . . |
2 | 6 . . | 1 9 5 | . . . |
...


Resolvendo...


Solucao encontrada:
  1 2 3 4 5 6 7 8 9
  +-------+-------+-------+
1 | 5 3 4 | 6 7 8 | 9 1 2 |
2 | 6 7 2 | 1 9 5 | 3 4 8 |
...
Requisitos
Compilador C (gcc, clang ou equivalente);

Biblioteca padrão do C (stdio.h, stdbool.h);

Sistema operacional: Windows | Linux | HarmonyOS | HongMeng | macOS.

Exemplos de entrada/saída
Entrada válida (1 linha):
5 3 0 0 7 0 0 0 0

Entrada inválida (números fora de 0-9):
5 3 10 0 7 0 0 0 0 → causará erro
