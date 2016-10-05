
import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintStream;
import java.util.Scanner;

public class JogoVida {

    static int contLive;

    static int nGeracoes;
    static int m;
    static int[][] matrizA;
    static int[][] matrizB;
    static Scanner entrada;

    public static void main(String[] args) {
        //entrada (.txt + quantidade de geracoes)
        try {
            nGeracoes = Integer.parseInt(args[0]);
            Input("teste.txt");
            LoadMatriz();
            StartGeneration();

            for (int i = 0; i < matrizA.length; i++) {
                for (int j = 0; j < matrizA[].length; j++) {
                    System.out.print(matrizA[i][j] + " ");
                }
                System.out.println();
            }
        } catch (FileNotFoundException e) {
            System.out.println("Arquivo nao encontrado, favor tentar novamente :)");
        }
        //geracao duas matriz (0 e 1) uma vai transcrever a outra alternando.
        //A inicia como o txt pediu.
        //A como com tamanho = quantidades de linhas X quantidade de linhas.
        // B tem msm tamanho que A.
        //LOOP(n vezes)
        //validando celulas e na matriz 0 e passando o valor pra matriz 1
        //trocar os numeros das matrizes (usando flag)
        //fim Loop
        //grava um arquivo com o resultado final
    }

    static void Input(String txt) throws FileNotFoundException {
        entrada = new Scanner(new File(txt));

        m = Integer.parseInt(entrada.nextLine());

        matrizA = new int[m][m];
        matrizB = new int[m][m];
        contLive = 0;
    }

    private static void LoadMatriz() {
        String[] temp = new String[matrizA.length];

        for (int i = 0; i < matrizA.length; i++) {
            temp[i] = entrada.nextLine();
            for (int j = 0; j < matrizA[].length; j++) {
                matrizA[i][j] = Character.getNumericValue(temp[i].charAt(j));
            }
        }
    }

    private static void StartGeneration() {

        for (int z = 0; z < nGeracoes; z++) {
            for (int i = 0; i < m; i++) {
                for (int j = 0; j < m; j++) {
                    //Primeira linha
                    if (i == 0) {
                        //PrimeiraLinha && primeira coluna
                        if (j == 0) {
                            //direita
                            if (matrizA[i][j + 1] == 1) {
                                contLive++;
                            }
                            //direita baixo
                            if (matrizA[i + 1][j + 1] == 1) {
                                contLive++;
                            }
                            //baixo
                            if (matrizA[i + 1][j] == 1) {
                                contLive++;
                            }
                            //Primeira Linha && ultima Coluna
                        } else if (j == m - 1) {
                            //esquerda
                            if (matrizA[i][j - 1] == 1) {
                                contLive++;
                            }
                            //esquerda Baixo
                            if (matrizA[i + 1][j - 1] == 1) {
                                contLive++;
                            }
                            //baixo
                            if (matrizA[i + 1][j] == 1) {
                                contLive++;
                            }
                            //primeira linha !primeiraColuna && !ultimaColuna
                        } else {
                            //esquerda
                            if (matrizA[i][j - 1] == 1) {
                                contLive++;
                            }
                            //direita
                            if (matrizA[i][j + 1] == 1) {
                                contLive++;
                            }
                            //BaixoEsquerda
                            if (matrizA[i + 1][j - 1] == 1) {
                                contLive++;
                            }
                            //Baixo
                            if (matrizA[i + 1][j] == 1) {
                                contLive++;
                            }
                            //BaixoDireita
                            if (matrizA[i + 1][j + 1] == 1) {
                                contLive++;
                            }
                        }
                        //ultima linha
                    } else if (i == m - 1) {
                        //UltimaLinha && Primeira coluna
                        if (j == 0) {
                            //cima
                            if (matrizA[i - 1][j] == 1) {
                                contLive++;
                            }
                            //cimaDireita
                            if (matrizA[i - 1][j + 1] == 1) {
                                contLive++;
                            }
                            //Direita
                            if (matrizA[i][j + 1] == 1) {
                                contLive++;
                            }
                            //UltimaLinha && ultima coluna
                        } else if (j == m - 1) {
                            //cima
                            if (matrizA[i - 1][j] == 1) {
                                contLive++;
                            }
                            //cimaEsquerda
                            if (matrizA[i - 1][j - 1] == 1) {
                                contLive++;
                            }
                            //esquerda
                            if (matrizA[i][j - 1] == 1) {
                                contLive++;
                            }
                        } //ultima linha && !primeiraColuna && !ultimaColuna
                        else {
                            //Esquerda
                            if (matrizA[i][j - 1] == 1) {
                                contLive++;
                            }
                            //Direita
                            if (matrizA[i][j + 1] == 1) {
                                contLive++;
                            }
                            //Cima
                            if (matrizA[i - 1][j] == 1) {
                                contLive++;
                            }
                            //CimaEsquerda
                            if (matrizA[i - 1][j - 1] == 1) {
                                contLive++;
                            }
                            //CimaDireita
                            if (matrizA[i - 1][j + 1] == 1) {
                                contLive++;
                            }
                        }
                    } //linhas do meio, aqui teram 3 formas diferente j == 0, j == m - 1, outros
                    else //meio && primeiraColuna
                    if (j == 0) {
                        //cima
                        if (matrizA[i - 1][j] == 1) {
                            contLive++;
                        }
                        //cimaDireita
                        if (matrizA[i - 1][j + 1] == 1) {
                            contLive++;
                        }
                        //Direita
                        if (matrizA[i][j + 1] == 1) {
                            contLive++;
                        }
                        //Baixo
                        if (matrizA[i + 1][j] == 1) {
                            contLive++;
                        }
                        //BaixoDireita
                        if (matrizA[i + 1][j + 1] == 1) {
                            contLive++;
                        }
                    } //Meio && Ultima Coluna
                    else if (j == m - 1) {
                        //cima
                        if (matrizA[i - 1][j] == 1) {
                            contLive++;
                        }
                        //cimaEsquerda
                        if (matrizA[i - 1][j - 1] == 1) {
                            contLive++;
                        }
                        //Esquerda
                        if (matrizA[i][j - 1] == 1) {
                            contLive++;
                        }
                        //Baixo
                        if (matrizA[i + 1][j] == 1) {
                            contLive++;
                        }
                        //BaixoEsquerda
                        if (matrizA[i + 1][j - 1] == 1) {
                            contLive++;
                        }
                    } //Meio && !primeiraColuna && !ultimaColuna
                    else {
                        //Cima
                        if (matrizA[i - 1][j] == 1) {
                            contLive++;
                        }
                        //CimaEsquerda
                        if (matrizA[i - 1][j - 1] == 1) {
                            contLive++;
                        }
                        //CimaDireita
                        if (matrizA[i - 1][j + 1] == 1) {
                            contLive++;
                        }
                        //Esquerda
                        if (matrizA[i][j - 1] == 1) {
                            contLive++;
                        }
                        //Direita
                        if (matrizA[i][j + 1] == 1) {
                            contLive++;
                        }
                        //Baixo
                        if (matrizA[i + 1][j] == 1) {
                            contLive++;
                        }
                        //BaixoEsquerda
                        if (matrizA[i + 1][j - 1] == 1) {
                            contLive++;
                        }
                        //BaixoDireita
                        if (matrizA[i + 1][j + 1] == 1) {
                            contLive++;
                        }
                    }
                    //validar o resultado e passar pra matrizB
                    /*
                    - Se a celula esta VIVA e tem menos de 2 ou mais de 3 vizinhos vivos ela MORRE.
                    - Uma celula VIVA, adjacente a 2 ou 3 celulas vivas permanece VIVA.
		    - Uma celula MORTA, adjacente a 2 ou 3 celulas vivas VIVE.
		    - Se a celula esta MORTA e tem menos de 2 ou mais de 3 vizinhos vivos ela continua MORTA.
                     */
                    //validacoes de viva
                    if (matrizA[i][j] == 1) {
                        if(contLive < 2 || contLive > 3)
                            matrizB[i][j] = 0;
                        else if(contLive == 2 || contLive == 3)
                            matrizB[i][j] = 1;
                    }
                    //validacoes  de morta
                    else{
                        if(contLive == 2 || contLive == 3)
                            matrizB[i][j] = 1;
                        else 
                            matrizB[i][j] = 0;
                    }
		    contLive = 0;
                }
            }
            matrizA = matrizB;
        }

    }

    private static void Write() throws FileNotFoundException {
        PrintStream destino = new PrintStream("result.txt");

        for (int i = 0; i < matrizA.length; i++) {
            for (int j = 0; j < matrizA[].length; j++) {
                destino.print(matrizA[i][j]);
            }
            destino.println();
        }
    }

}
