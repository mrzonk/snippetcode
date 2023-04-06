```java
package Database;

import com.mysql.jdbc.jdbc2.optional.MysqlDataSource;
import java.sql.Connection;
import java.sql.SQLException;
import javax.swing.JOptionPane;
/**
 *
 * @author Rahul Ramadani
 */
public class koneksi {
    private static Connection koneksi;
    
    
    public static Connection koneksiDatabase(){
        if(koneksi==null){
            MysqlDataSource dataSource = new MysqlDataSource();
            dataSource.setURL("jdbc:mysql://localhost/activ");
            dataSource.setUser("root");
            dataSource.setPassword("");
            try{
                koneksi = dataSource.getConnection();
            }catch (SQLException ex) {
                JOptionPane.showMessageDialog(null,"Error Koneksi :"+ ex.getMessage());
            }
        }
        return koneksi;
    }
    public Connection getConnection(){
        throw new UnsupportedOperationException("Not Supported yet.");
    }
}


```
