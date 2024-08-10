import java.security.SecureRandom;
import java.util.Scanner;

public class AdvancedPasswordGenerator {
    private static final String UPPER_CASE = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    private static final String LOWER_CASE = "abcdefghijklmnopqrstuvwxyz";
    private static final String NUMBERS = "0123456789";
    private static final String SPECIAL_CHARS = "!@#$%^&*()_+-=[]|,./?><";
    private static final SecureRandom random = new SecureRandom();

    // Custom exception class
    static class InsufficientLengthException extends Exception {
        public InsufficientLengthException(String message) {
            super(message);
        }
    }

    // Generate a single random character from a given category
    private static char getRandomChar(String category) {
        return category.charAt(random.nextInt(category.length()));
    }

    public static String generatePassword(int length, int minUpper, int minLower, int minDigits, int minSpecial) throws InsufficientLengthException {
        if (minUpper + minLower + minDigits + minSpecial > length) {
            throw new InsufficientLengthException("Error: Total minimum required characters exceed the total length of the password.");
        }

        StringBuilder password = new StringBuilder(length);
        // Add minimum required characters of each type
        for (int i = 0; i < minUpper; i++) {
            password.append(getRandomChar(UPPER_CASE));
        }
        for (int i = 0; i < minLower; i++) {
            password.append(getRandomChar(LOWER_CASE));
        }
        for (int i = 0; i < minDigits; i++) {
            password.append(getRandomChar(NUMBERS));
        }
        for (int i = 0; i < minSpecial; i++) {
            password.append(getRandomChar(SPECIAL_CHARS));
        }

        // Fill the rest with random characters from all types
        String allChars = UPPER_CASE + LOWER_CASE + NUMBERS + SPECIAL_CHARS;
        while (password.length() < length) {
            password.append(getRandomChar(allChars));
        }

        // Shuffle the characters to distribute the types randomly
        char[] passwordArray = password.toString().toCharArray();
        for (int i = passwordArray.length - 1; i > 0; i--) {
            int index = random.nextInt(i + 1);
            char temp = passwordArray[index];
            passwordArray[index] = passwordArray[i];
            passwordArray[i] = temp;
        }

        return new String(passwordArray);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter the desired total length for your password: ");
        int length = scanner.nextInt();
        System.out.print("Minimum number of uppercase letters: ");
        int minUpper = scanner.nextInt();
        System.out.print("Minimum number of lowercase letters: ");
        int minLower = scanner.nextInt();
        System.out.print("Minimum number of digits: ");
        int minDigits = scanner.nextInt();
        System.out.print("Minimum number of special characters: ");
        int minSpecial = scanner.nextInt();

        try {
            String password = generatePassword(length, minUpper, minLower, minDigits, minSpecial);
            System.out.println("Generated Password: " + password);
        } catch (InsufficientLengthException e) {
            System.out.println(e.getMessage());
        }
        scanner.close();
    }
}
