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




