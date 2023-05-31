Втора лабораториска вежба по Софтверско инженерство

Стефан Вељаноски, бр. на индекс 213098

Control Flow Graph
![slikasi](https://github.com/svelj/SI_lab2_213098/assets/126978134/8f99d8e4-f85b-4947-bae5-3fc5a3e83de1)


Цикломатска комплексност
Цикломатската комплексност на овој код е 10 истата ја добив преку формулата P+1, каде што P е бројот на предикатни јазли. Во случајoв P=9, па цикломатската комплексност изнесува 10.

Тест случаи според критериумот Every Branch
     // Test Case 1
        assertThrows(RuntimeException.class, () -> {
            User user = null;
            List<User> allUsers = new ArrayList<>();
            SILab2.function(user, allUsers);
        });

        // Test Case 2
        assertThrows(RuntimeException.class, () -> {
            User user = new User("username", "password", null);
            List<User> allUsers = new ArrayList<>();
            SILab2.function(user, allUsers);
        });

        // Test Case 3
        assertThrows(RuntimeException.class, () -> {
            User user = new User("username", null, "example@email.com");
            List<User> allUsers = new ArrayList<>();
            SILab2.function(user, allUsers);
        });

        // Test Case 4
        User user = new User(null, "password", "example@email.com");
        SILab2.function(user, null);
        assertEquals("example@example.com", user.getEmail());

        // Test Case 5
        List<User> allUsers = new ArrayList<>();
        user = new User("username", "password", "example@email.com");
        User existingUser1 = new User("username", "password", "example@email.com");
        User existingUser2 = new User("username", "password", "other@email.com");
        allUsers.add(existingUser1);
        allUsers.add(existingUser2);
        boolean result = SILab2.function(user, allUsers);
        assertTrue(result);

        // Test Case 6
        user = new User("example@example.com", "password", "example@example.com");
        allUsers = new ArrayList<>();
        existingUser1 = new User("other@example.com", "password", "other@example.com");
        existingUser2 = new User("other2@example.com", "password", "other2@example.com");
        allUsers.add(existingUser1);
        allUsers.add(existingUser2);
        result = SILab2.function(user, allUsers);
        assertTrue(result);

        // Test Case 7
        user = new User("username", "password", "example@email.com");
        result = SILab2.function(user, null);
        assertTrue(result);

        // Test Case 8
        user = new User("username with special characters !@#$", "password", "example@email.com");
        result = SILab2.function(user, null);
        assertFalse(result);

        // Test Case 9
        user = new User("username", "short", null);
        result = SILab2.function(user, null);
        assertFalse(result);
Тест случаи според критериумот Multiple Condition
    Test case 1: T T T
        User user1 = new User("username", "password", "example@email.com");
        assertDoesNotThrow(() -> SILab2.function(user1, allUsers));

//        Test case 2: T T F
        User user2 = new User("username", "password", null);
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user2, allUsers);
        });

//        Test case 3: T F T
        User user3 = new User("username", null, "example@email.com");
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user3, allUsers);
        });

//        Test case 4: T F F
        User user4 = new User("username", null, null);
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user4, allUsers);
        });

//        Test case 5: F T T
        User user5 = new User(null, "password", "example@email.com");
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user5, allUsers);
        });

//        Test case 6: F T F
        User user6 = new User(null, "password", null);
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user6, allUsers);
        });

//        Test case 7: F F T
        User user7 = new User(null, null, "example@email.com");
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user7, allUsers);
        });

//        Test case 8: F F F
        User user8 = new User(null, null, null);
        assertThrows(RuntimeException.class, () -> {
            SILab2.function(user8, allUsers);
        });
