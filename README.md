# rajdemo
<br>
author-rishirajsingh(java support er)
package practise;

 
import java.sql.*;

public class Jdvc {
    public static void main(String[] args) {
        String url = " jdbc:mysql://127.0.0.1/test_api"; // change db name
        String user = "root";
        String password = "Rishi@123"; // change your password

        try {
            // 1. Load the driver (optional for newer versions)
            Class.forName( "com.mysql.cj.jdbc.Driver");

            // 2. Connect to the database
            Connection conn = DriverManager.getConnection(url, user, password);
            System.out.println("Connected to DB");

            // 3. INSERT
            String insert = "INSERT INTO users (id, name, email,job) VALUES (?, ?, ?,?)";
            PreparedStatement psInsert = conn.prepareStatement(insert);
            psInsert.setInt(1, 5);
            psInsert.setString(2, "Rishi r");
            psInsert.setString(3, "rishssssi@example.com");
            psInsert.setString(4, " fnbnbfhs");
            psInsert.executeUpdate();
            System.out.println("Record Inserted");

            // 4. SELECT
            String select = "SELECT * FROM users";
            Statement stmt = conn.createStatement();
            ResultSet rs = stmt.executeQuery(select);
            while (rs.next()) {
                System.out.println("ID: " + rs.getInt("id") +
                                   ", Name: " + rs.getString("name") +
                                   ", Email: " + rs.getString("email"));
            }

			/*
			 * // 5. UPDATE String update = "UPDATE users SET email = ? WHERE id = ?";
			 * PreparedStatement psUpdate = conn.prepareStatement(update);
			 * psUpdate.setString(1, "rishi_updated@example.com"); psUpdate.setInt(2, 1);
			 * psUpdate.executeUpdate(); System.out.println("Record Updated");
			 */

            // 6. DELETE
			/*
			 * String delete = "DELETE FROM users WHERE id = ?"; PreparedStatement psDelete
			 * = conn.prepareStatement(delete); psDelete.setInt(1, 1);
			 * psDelete.executeUpdate(); System.out.println("Record Deleted");
			 */

            // 7. Close connection
            conn.close();
            System.out.println("Connection closed.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}


