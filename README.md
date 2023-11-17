//blowfish
import javax.crypto.Cipher;
import javax.crypto.spec.SecretKeySpec;

public class cns2 {
    public static void main(String[] args) {
            try {
                String keyString = "ThisIsASecretKey";
                byte[] keyData = keyString.getBytes();
                Cipher cipher = Cipher.getInstance("Blowfish");
                SecretKeySpec secretKeySpec = new SecretKeySpec(keyData, "Blowfish");
                cipher.init(Cipher.ENCRYPT_MODE, secretKeySpec);
                String data = "Hello, Blowfish!";
                byte[] encryptedData = cipher.doFinal(data.getBytes());
                System.out.println("Original data: " + data);
                System.out.println("Encrypted data: " + new String(encryptedData));
                cipher.init(Cipher.DECRYPT_MODE, secretKeySpec);
                byte[] decryptedData = cipher.doFinal(encryptedData);
                System.out.println("Decrypted data: " + new String(decryptedData));
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }

//AesDes

import javax.crypto.Cipher;
import javax.crypto.KeyGenerator;
import javax.crypto.SecretKey;
import java.util.Base64;


class DESExample{
    public static void main(String[] args) {
        try{
            KeyGenerator kg = KeyGenerator.getInstance("AES");
            SecretKey myDESKey = kg.generateKey();
            Cipher cipher =     Cipher.getInstance("AES/ECB/PKCS5Padding");
            cipher.init(Cipher.ENCRYPT_MODE, myDESKey);
            byte[] text = "iamnotinvincible".getBytes();
            byte[] textEnc = cipher.doFinal(text);
            System.out.println("Text in bytes: "+ textEnc);
            System.out.println("Text in encrypted: "+ new String((textEnc)));
            Cipher decryptCipher = Cipher.getInstance("AES/ECB/PKCS5Padding");
            decryptCipher.init(Cipher.DECRYPT_MODE, myDESKey);
            byte[] textDec = decryptCipher.doFinal(textEnc);
            System.out.println("Decrypted Text: "+ new String(textDec));
    }
        catch(Exception e) {
            e.printStackTrace();
        }
    }
}

public class CaesarCipher {
    public static void main(String[] args) {
        String plaintext = "Hello, World!";
        int shiftKey = 3;

        // Encryption
        String encryptedText = encrypt(plaintext, shiftKey);
        System.out.println("Encrypted Text: " + encryptedText);

        // Decryption
        String decryptedText = decrypt(encryptedText, shiftKey);
        System.out.println("Decrypted Text: " + decryptedText);
    }

    // Encryption method
    public static String encrypt(String plaintext, int shiftKey) {
        StringBuilder ciphertext = new StringBuilder();

        for (int i = 0; i < plaintext.length(); i++) {
            char ch = plaintext.charAt(i);

            if (Character.isLetter(ch)) {
                char encryptedChar = (char) ((ch + shiftKey - 'A') % 26 + 'A');
                ciphertext.append(encryptedChar);
            } else {
                ciphertext.append(ch);
            }
        }

        return ciphertext.toString();
    }

    // Decryption method
    public static String decrypt(String ciphertext, int shiftKey) {
        StringBuilder decryptedText = new StringBuilder();

        for (int i = 0; i < ciphertext.length(); i++) {
            char ch = ciphertext.charAt(i);

            if (Character.isLetter(ch)) {
                char decryptedChar = (char) ((ch - shiftKey - 'A' + 26) % 26 + 'A');
                decryptedText.append(decryptedChar);
            } else {
                decryptedText.append(ch);
            }
        }

        return decryptedText.toString();
    }
}



//andandxor
class cns3{
    public static void main(String[] args) {
        String input = "Hello world";
        System.out.println("Original String: " + input );

        String resultString = andXorWith127(input);

        System.out.println("Result String: ");
        printAsciiValues(resultString);
    }

    private static String andXorWith127(String input) {
        char[] charArray = input.toCharArray();

        for (int i = 0; i < charArray.length; i++){
            charArray[i] = (char) (charArray[i] & 127);
            charArray[i] = (char) (charArray[i] ^ 127);
        }
        return new String(charArray);
    }
    private static void printAsciiValues(String input) {
        for (char c : input.toCharArray()){
            System.out.println((int) c + " ");
        }
    }
}




