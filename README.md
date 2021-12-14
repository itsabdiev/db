```java
package com.company;

import java.sql.*;

public class Main {

    public static void main(String[] args) {
            String jdbcURL = "jdbc:postgresql://ec2-52-48-137-75.eu-west-1.compute.amazonaws.com:5432/d3g3g6r529vc82";
            String username = "ncxfuopnggexwd";
        try {
            Connection connection = DriverManager.getConnection(jdbcURL,username,password);
            System.out.println("Connected to Postgresql server successfully");
            String inserting= "INSERT INTO users(nick,score) VALUES ('elmir','7000')";
            Statement statement = connection.createStatement();
            statement.executeUpdate(inserting);

            String query = "SELECT * FROM users";
            ResultSet resultSet = statement.executeQuery(query);
            while(resultSet.next()) {
                String nickname = resultSet.getString("nick");
                String score = resultSet.getString("score");
                System.out.printf("nickname - %s | score - %s",nickname,score);
                System.out.println("");
            }

            connection.close();
        } catch (SQLException throwables) {
            System.out.println("Error in connecting to Postgresql server");
            throwables.printStackTrace();
        }
    }

}

```

https://github.com/diogoalex01/FEUP-LBAW/blob/master/resources/sql/database.sql
