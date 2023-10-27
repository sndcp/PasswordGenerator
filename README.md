

import java.util.Random;
import java.util.Scanner;

public class PasswordGenerator {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        char buyukHarf;
        do {
            System.out.print("Bir büyük harf girin: ");
            buyukHarf = scanner.nextLine().charAt(0);
        } while (buyukHarf < 'A' || buyukHarf > 'Z');

        char kucukHarf;
        do {
            System.out.print("Bir küçük harf girin: ");
            kucukHarf = scanner.nextLine().charAt(0);
        } while (kucukHarf < 'a' || kucukHarf > 'z');

        int ikiSayi;
        do {
            System.out.print("Bir çift basamaklı sayı girin: ");
            ikiSayi = scanner.nextInt();
        } while (ikiSayi < 10 || ikiSayi > 99);

        char ozelSimge;
        do {
            System.out.print("Bir özel simge girin: ");
            ozelSimge = scanner.next().charAt(0);
        } while (ozelKarakterVarMi(ozelSimge) == false);

        scanner.close();

        String randomHarfveSayilar = generateRandomString(5);

        String sifre = String.valueOf(buyukHarf) + String.valueOf(kucukHarf) + randomHarfveSayilar + String.valueOf(ikiSayi) + String.valueOf(ozelSimge);
        System.out.println("Şifre: " + sifre);
    }

    public static String generateRandomString(int length) {
        String characters = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
        StringBuilder sb = new StringBuilder(length);
        Random random = new Random();

        for (int i = 0; i < length; i++) {
            int index = random.nextInt(characters.length());
            sb.append(characters.charAt(index));
        }

        return sb.toString();
    }

    public static boolean ozelKarakterVarMi(char c) {
        return (c >= 33 && c <= 47) || (c >= 58 && c <= 64) || (c >= 91 && c <= 96) || (c >= 123 && c <= 126);
    }
}

