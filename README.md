# prueba-1q2
import java.util.ArrayList;
import java.util.Scanner;

public class Palindromo {
    public static void main(String[] args) {
        String[] palabras = { 
            "radar", "level", "world", "civic", "java", "deified", 
            "python", "rotor", "language", "madam", "refer", "stats", 
            "noon", "hello", "moon", "wow", "racecar", "kayak", "apple", "deed" 
        };

        System.out.println("Lista de Palabras:");
        for (int i = 0; i < palabras.length; i++) {
            System.out.println("[" + i + "]: " + palabras[i]);
        }

        Scanner scanner = new Scanner(System.in);
        
        System.out.print("\nIngresar el tamaño de la listas: ");
        int n = scanner.nextInt();

        String[] listaA = new String[n];
        String[] listaB = new String[n];

        System.out.println("\nLista Palabras Palíndroma listaA:");
        int contadorA = 0;
        for (int i = 0; i < n; i++) {
            listaA[i] = palabras[i];  
            if (esPalindromo(listaA[i])) {
                System.out.println("[" + contadorA + "]: " + listaA[i]);
                contadorA++;
            }
        }
        
        System.out.println("\nLista Palabras Palíndroma listaB:");
        int contadorB = 0;
        for (int i = n; i < 2 * n; i++) {
            listaB[i - n] = palabras[i];  
            if (esPalindromo(listaB[i - n])) {
                System.out.println("[" + contadorB + "]: " + listaB[i - n]);
                contadorB++;
            }
        }
        
        ArrayList<String> diferencia = new ArrayList<>();
        for (int i = 0; i < n; i++) {
            boolean estaEnB = false;
            for (int j = 0; j < n; j++) {
                if (listaA[i].equals(listaB[j])) {
                    estaEnB = true;
                    break;
                }
            }
            if (!estaEnB) {
                diferencia.add(listaA[i]);
            }
        }
        
        System.out.println("\nPalabras del listaA no están en el listaB son:");
        for (int i = 0; i < diferencia.size(); i++) {
            System.out.println("[" + i + "]: " + diferencia.get(i));
        }
        
        scanner.close();
    }
    
    public static boolean esPalindromo(String palabra) {
        int inicio = 0;
        int fin = palabra.length() - 1;
        
        while (inicio < fin) {
            if (palabra.charAt(inicio) != palabra.charAt(fin)) {
                return false;
            }
            inicio++;
            fin--;
        }
        
        return true;
    }
}
