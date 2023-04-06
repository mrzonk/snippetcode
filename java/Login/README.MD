#Btn CLICK
```java
 private void btnLoginActionPerformed(java.awt.event.ActionEvent evt) {                                         
        String user = txtUsername.getText();
        String pass = String.valueOf(pfPassword.getPassword());
        if (user.trim().equals("")){
            JOptionPane.showMessageDialog(this, "Username Tidak Boleh Kosong");
        }else if (pass.trim().equals("")){
            JOptionPane.showMessageDialog(this, "Password Tidak Boleh Kosong");
        }else validasi (user, pass);
    }                                        

```

```java
 public void validasi (String user, String pass){
    String query = "SELECT*FROM user WHERE user=? AND password=?";
    PreparedStatement statement;
    Connection connection;
    
    try {
        connection = koneksi.koneksiDatabase();
        statement = connection.prepareStatement(query);
        statement.setString(1, user);
        statement.setString(2, pass);
        ResultSet rs = statement.executeQuery();
        if(rs.next()){
            this.dispose();
            new MainMenu().setVisible(true);
        }else{
            JOptionPane.showMessageDialog(this, "Username Atau Password Salah");
        }
    }catch(SQLException err){
        JOptionPane.showMessageDialog(this, "Terjadi Kesalahan :" + err.getMessage());
        
    }
    
    }


```


