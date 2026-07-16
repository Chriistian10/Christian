# Calculadora de IMC
calculadora de IMC
import java.util.Locale;
import java.util.Scanner;

public class CalculadoraIMC {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        scanner.useLocale(Locale.US); // aceita ponto decimal (ex: 1.75)

        System.out.println("=== Calculadora de IMC ===");

        System.out.print("Digite seu peso (kg): ");
        double peso = lerDouble(scanner);

        System.out.print("Digite sua altura (m), ex: 1.75: ");
        double altura = lerDouble(scanner);

        if (peso <= 0 || altura <= 0) {
            System.out.println("Peso e altura devem ser valores positivos.");
            return;
        }

        double imc = calcularIMC(peso, altura);
        String classificacao = classificarIMC(imc);

        System.out.printf("%nSeu IMC é: %.2f%n", imc);
        System.out.println("Classificação: " + classificacao);

        scanner.close();
    }

    private static double lerDouble(Scanner scanner) {
        while (!scanner.hasNextDouble()) {
            System.out.print("Valor inválido. Digite novamente: ");
            scanner.next();
        }
        return scanner.nextDouble();
    }

    private static double calcularIMC(double peso, double altura) {
        return peso / (altura * altura);
    }

    private static String classificarIMC(double imc) {
        if (imc < 18.5) {
            return "Abaixo do peso";
        } else if (imc < 25) {
            return "Peso normal";
        } else if (imc < 30) {
            return "Sobrepeso";
        } else if (imc < 35) {
            return "Obesidade grau I";
        } else if (imc < 40) {
            return "Obesidade grau II";
        } else {
            return "Obesidade grau III";
        }
    }
}
