import java.util.HashMap;
import java.util.Map;
import java.util.TreeMap;

public class PhoneBook {
    public static void main(String[] args) {
        Map<String, String> phoneBook = new HashMap<>();
        phoneBook.put("Иванов", "123-45-67");
        phoneBook.put("Петров", "234-56-78");
        phoneBook.put("Сидоров", "345-67-89");
        phoneBook.put("Иванов", "456-78-90");

        Map<String, Integer> phoneBookCount = new HashMap<>();
        for (String name : phoneBook.keySet()) {
            if (phoneBookCount.containsKey(name)) {
                phoneBookCount.put(name, phoneBookCount.get(name) + 1);
            } else {
                phoneBookCount.put(name, 1);
            }
        }

        Map<Integer, String> sortedPhoneBookCount = new TreeMap<>(Collections.reverseOrder());
        for (Map.Entry<String, Integer> entry : phoneBookCount.entrySet()) {
            sortedPhoneBookCount.put(entry.getValue(), entry.getKey());
        }

        for (Map.Entry<Integer, String> entry : sortedPhoneBookCount.entrySet()) {
            System.out.println(entry.getValue() + ": " + phoneBook.get(entry.getValue()));
        }
    }
}
