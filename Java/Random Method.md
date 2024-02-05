# Random Class

### 1. **Creating an Instance:**
   ```java
   Random random = new Random();
   ```

### 2. **Generating Random Integers:**
   ```java
   int randomNumber = random.nextInt(); // Generates a random integer
   int rangeRandom = random.nextInt(max - min + 1) + min; // Generates a random integer in the specified range [min, max]
   ```

### 3. **Generating Random Longs:**
   ```java
   long randomLong = random.nextLong(); // Generates a random long
   ```

### 4. **Generating Random Doubles:**
   ```java
   double randomDouble = random.nextDouble(); // Generates a random double between 0.0 (inclusive) and 1.0 (exclusive)
   ```

### 5. **Generating Gaussian (Normal) Distribution:**
   ```java
   double gaussianValue = random.nextGaussian(); // Generates a random value following a Gaussian distribution with mean 0 and standard deviation 1
   ```

### 6. **Setting Seed for Reproducibility:**
   ```java
   long seed = 123L;
   Random seededRandom = new Random(seed); // Use the same seed to get reproducible sequences
   ```

### 7. **Shuffling an Array:**
   ```java
   int[] array = {1, 2, 3, 4, 5};
   Collections.shuffle(Arrays.asList(array), random); // Shuffles the array using the provided random instance
   ```

### 8. **Picking a Random Element from an Array or List:**
   ```java
   int[] array = {1, 2, 3, 4, 5};
   int randomElement = array[random.nextInt(array.length)]; // Picks a random element from the array
   ```

### 9. **Random Boolean:**
   ```java
   boolean randomBoolean = random.nextBoolean(); // Generates a random boolean
   ```

### 10. **Random UUID:**
   ```java
   UUID randomUUID = UUID.randomUUID(); // Generates a random UUID
   ```

### 11. **Thread-Safe Random:**
   ```java
   SecureRandom secureRandom = new SecureRandom(); // Thread-safe random numbers
   ```

### 12. **Random Color (for JavaFX or AWT/Swing):**
   ```java
   Color randomColor = new Color(random.nextInt(256), random.nextInt(256), random.nextInt(256));
   ```

### 13. **Dice Roll Simulation:**
   ```java
   int diceRoll = random.nextInt(6) + 1; // Simulates a dice roll (1 to 6)
   ```

### 14. **Random Password Generation:**
   ```java
   String upper = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";
   String lower = "abcdefghijklmnopqrstuvwxyz";
   String digits = "0123456789";
   String special = "!@#$%^&*()-_+=<>?";

   String password = upper + lower + digits + special;
   char[] passwordArray = password.toCharArray();
   for (int i = 0; i < length; i++) {
       char randomChar = passwordArray[random.nextInt(passwordArray.length)];
       // Use randomChar in password generation logic
   }
   ```

### 15. **Random Date within a Range:**
   ```java
   LocalDate start = LocalDate.of(2020, 1, 1);
   LocalDate end = LocalDate.of(2022, 12, 31);
   long randomEpochDay = ThreadLocalRandom.current().nextLong(start.toEpochDay(), end.toEpochDay());
   LocalDate randomDate = LocalDate.ofEpochDay(randomEpochDay);
   ```