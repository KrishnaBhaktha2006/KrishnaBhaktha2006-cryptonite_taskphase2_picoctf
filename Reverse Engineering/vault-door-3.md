# vault-door-3

*Flag:* picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_c79a21}

How you approached the challenge:

- step 1: I opened the file it was coded in java I know c++ and had tried to learn java between 12 and engineering so i kind of got idea of the code
```
import java.util.*;

class VaultDoor3 {
    public static void main(String args[]) {
        VaultDoor3 vaultDoor = new VaultDoor3();
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter vault password: ");
        String userInput = scanner.next();
	String input = userInput.substring("picoCTF{".length(),userInput.length()-1);
	if (vaultDoor.checkPassword(input)) {
	    System.out.println("Access granted.");
	} else {
	    System.out.println("Access denied!");
        }
    }

    // Our security monitoring team has noticed some intrusions on some of the
    // less secure doors. Dr. Evil has asked me specifically to build a stronger
    // vault door to protect his Doomsday plans. I just *know* this door will
    // keep all of those nosy agents out of our business. Mwa ha!
    //
    // -Minion #2671
    public boolean checkPassword(String password) {
        if (password.length() != 32) {
            return false;
        }
        char[] buffer = new char[32];
        int i;
        for (i=0; i<8; i++) {
            buffer[i] = password.charAt(i);
        }
        for (; i<16; i++) {
            buffer[i] = password.charAt(23-i);
        }
        for (; i<32; i+=2) {
            buffer[i] = password.charAt(46-i);
        }
        for (i=31; i>=17; i-=2) {
            buffer[i] = password.charAt(i);
        }
        String s = new String(buffer);
        return s.equals("jU5t_a_sna_3lpm12g94c_u_4_m7ra41");
    }
}

```
This was the code i directly jumped into checkPassword i think it needed an input so i was kinda sure "jU5t_a_sna_3lpm12g94c_u_4_m7ra41" was the input anyways i then traced to the forloop and i got a different format "jU5t_a_s1mpl3_an4gr4m_4_u_c79a21"
Something like this and when i enclosed it in picoCTF{..} flag boom i got flag.!! 

What you learned through solving this challenge:

1. We need To know the basics of coding

Other incorrect methods you tried:

- tried running the program
- Tried coding a new program but realised i am unskilled in java

References

- No reference
