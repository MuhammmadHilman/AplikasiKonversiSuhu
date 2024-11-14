# Aplikasi Konversi Suhu

Tugas 2 - Aplikasi Konversi Suhu

# Deskripsi
Aplikasi Konversi Suhu ini adalah program GUI sederhana yang dibuat menggunakan Java Swing dan NetBeans untuk membantu melakukan konversi suhu antara beberapa skala: Celcius, Fahrenheit, Reamur, dan Kelvin.


# Features

Fitur tambahan dari aplikasi ini meliputi:

1. Input Suhu: Pengguna dapat memasukkan suhu yang ingin dikonversi.
2. Pilih Skala Awal: Pengguna dapat memilih skala awal suhu yang ingin dikonversi (Celcius, Fahrenheit, Kelvin, atau Reamur).
3. Pilih Skala Tujuan: Pengguna dapat memilih skala tujuan untuk konversi suhu (Celcius, Fahrenheit, Kelvin, atau Reamur).
4. Konversi Otomatis: Aplikasi secara otomatis mengonversi suhu setelah input atau pilihan skala berubah.
5. Tombol Konversi Manual: Pengguna juga dapat memilih untuk melakukan konversi dengan menekan tombol "Konversi".
6. Hasil Konversi: Hasil konversi ditampilkan dalam bentuk teks di area output.


# Dokumentasi Code

```java

import javax.swing.event.DocumentEvent;
import javax.swing.event.DocumentListener;

/**
 *
 * @author Hilman
 */
public class AplikasiKonversiSuhu extends javax.swing.JFrame {

    /**
     * Creates new form AplikasiKonversiSuhu
     */
    public AplikasiKonversiSuhu() {
        initComponents();
        txt_suhu.getDocument().addDocumentListener(new DocumentListener() {
            @Override
            public void insertUpdate(DocumentEvent e) {
                konversiSuhu();
            }

            @Override
            public void removeUpdate(DocumentEvent e) {
                konversiSuhu();
            }

            @Override
            public void changedUpdate(DocumentEvent e) {
                konversiSuhu();
            }
        });

        // Add action listeners to radio buttons and combo box for real-time conversion on selection change
        radio_celcius.addActionListener(e -> konversiSuhu());
        radio_fahrenheit.addActionListener(e -> konversiSuhu());
        radio_reamur.addActionListener(e -> konversiSuhu());
        radio_kelvin.addActionListener(e -> konversiSuhu());
        combo_asal.addActionListener(e -> konversiSuhu());
        
        btn_konversi.addActionListener(e -> konversiSuhu());
        
    }
    
    private void konversiSuhu() {
    try {
        // Get the input temperature from the text field
        double suhu = Double.parseDouble(txt_suhu.getText().trim());

        // Check if the combo box has a selected item
        if (combo_asal.getSelectedItem() == null) {
            txt_hasil.setText("Silakan pilih satuan asal.");
            return;
        }

        // Get the selected original unit from the combo box
        String asal = combo_asal.getSelectedItem().toString();

        // Determine the target unit based on the selected radio button
        String tujuan = "";
        if (radio_celcius.isSelected()) {
            tujuan = "Celsius";
        } else if (radio_fahrenheit.isSelected()) {
            tujuan = "Fahrenheit";
        } else if (radio_kelvin.isSelected()) {
            tujuan = "Kelvin";
        } else if (radio_reamur.isSelected()) {
            tujuan = "Reaumur";
        } else {
            txt_hasil.setText("Silakan Pilih Suhu.");
            return;
        }

        double hasil = 0.0;
        
        
        if (asal.equals("Celcius")) {
            switch (tujuan) {
                case "Fahrenheit": hasil = (suhu * 9 / 5) + 32; break;
                case "Kelvin": hasil = suhu + 273.15; break;
                case "Reaumur": hasil = suhu * 4 / 5; break;
                case "Celsius": hasil = suhu; break;
            }
        } else if (asal.equals("Fahrenheit")) {
            switch (tujuan) {
                case "Celsius": hasil = (suhu - 32) * 5 / 9; break;
                case "Kelvin": hasil = (suhu - 32) * 5 / 9 + 273.15; break;
                case "Reaumur": hasil = (suhu - 32) * 4 / 9; break;
                case "Fahrenheit": hasil = suhu; break;
            }
        } else if (asal.equals("Kelvin")) {
            switch (tujuan) {
                case "Celsius": hasil = suhu - 273.15; break;
                case "Fahrenheit": hasil = (suhu - 273.15) * 9 / 5 + 32; break;
                case "Reaumur": hasil = (suhu - 273.15) * 4 / 5; break;
                case "Kelvin": hasil = suhu; break;
            }
        } else if (asal.equals("Reamur")) {
            switch (tujuan) {
                case "Celsius": hasil = suhu * 5 / 4; break;
                case "Fahrenheit": hasil = (suhu * 9 / 4) + 32; break;
                case "Kelvin": hasil = suhu * 5 / 4 + 273.15; break;
                case "Reaumur": hasil = suhu; break;
            }
        }

        // Display the result in the result text field
        txt_hasil.setText(String.format("%.2f", hasil));

    } catch (NumberFormatException e) {
        // Display an error message if the input is invalid
        txt_hasil.setText("Inputan tidak valid");
    }
    }
    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {
        java.awt.GridBagConstraints gridBagConstraints;

        buttonGroup1 = new javax.swing.ButtonGroup();
        jPanel1 = new javax.swing.JPanel();
        jLabel1 = new javax.swing.JLabel();
        jLabel2 = new javax.swing.JLabel();
        btn_konversi = new javax.swing.JButton();
        txt_suhu = new javax.swing.JTextField();
        txt_hasil = new javax.swing.JTextField();
        combo_asal = new javax.swing.JComboBox<>();
        jLabel3 = new javax.swing.JLabel();
        jLabel4 = new javax.swing.JLabel();
        radio_celcius = new javax.swing.JRadioButton();
        radio_fahrenheit = new javax.swing.JRadioButton();
        radio_reamur = new javax.swing.JRadioButton();
        radio_kelvin = new javax.swing.JRadioButton();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);

        jPanel1.setBorder(javax.swing.BorderFactory.createTitledBorder(null, "Aplikasi Konversi Suhu", javax.swing.border.TitledBorder.DEFAULT_JUSTIFICATION, javax.swing.border.TitledBorder.DEFAULT_POSITION, new java.awt.Font("Tahoma", 1, 14))); // NOI18N
        jPanel1.setLayout(new java.awt.GridBagLayout());

        jLabel1.setText("Masukkan Suhu");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(29, 34, 0, 0);
        jPanel1.add(jLabel1, gridBagConstraints);

        jLabel2.setText("Hasil Konversi");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 5;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(9, 42, 0, 0);
        jPanel1.add(jLabel2, gridBagConstraints);

        btn_konversi.setText("Konversi");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 2;
        gridBagConstraints.gridy = 7;
        gridBagConstraints.gridwidth = 5;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(27, 36, 37, 0);
        jPanel1.add(btn_konversi, gridBagConstraints);

        txt_suhu.addKeyListener(new java.awt.event.KeyAdapter() {
            public void keyTyped(java.awt.event.KeyEvent evt) {
                txt_suhuKeyTyped(evt);
            }
        });
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.fill = java.awt.GridBagConstraints.HORIZONTAL;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(26, 10, 0, 0);
        jPanel1.add(txt_suhu, gridBagConstraints);

        txt_hasil.setEditable(false);
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 5;
        gridBagConstraints.gridwidth = 9;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.fill = java.awt.GridBagConstraints.HORIZONTAL;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(9, 10, 0, 0);
        jPanel1.add(txt_hasil, gridBagConstraints);

        combo_asal.setModel(new javax.swing.DefaultComboBoxModel<>(new String[] { "Pilih Asal", "Celcius", "Fahrenheit", "Reamur", "Kelvin" }));
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 10;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.gridwidth = 7;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(26, 2, 0, 103);
        jPanel1.add(combo_asal, gridBagConstraints);

        jLabel3.setText("Pilih Suhu");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 6;
        gridBagConstraints.gridy = 0;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(29, 2, 0, 0);
        jPanel1.add(jLabel3, gridBagConstraints);

        jLabel4.setText("Pilih Konversi");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 0;
        gridBagConstraints.gridy = 2;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(22, 46, 0, 0);
        jPanel1.add(jLabel4, gridBagConstraints);

        buttonGroup1.add(radio_celcius);
        radio_celcius.setText("Celcius");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 2;
        gridBagConstraints.gridwidth = 2;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(18, 10, 0, 0);
        jPanel1.add(radio_celcius, gridBagConstraints);

        buttonGroup1.add(radio_fahrenheit);
        radio_fahrenheit.setText("Fahrenheit");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 5;
        gridBagConstraints.gridy = 2;
        gridBagConstraints.gridwidth = 6;
        gridBagConstraints.gridheight = 2;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(18, 2, 0, 0);
        jPanel1.add(radio_fahrenheit, gridBagConstraints);

        buttonGroup1.add(radio_reamur);
        radio_reamur.setText("Reamur");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 1;
        gridBagConstraints.gridy = 4;
        gridBagConstraints.gridwidth = 3;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(3, 10, 0, 0);
        jPanel1.add(radio_reamur, gridBagConstraints);

        buttonGroup1.add(radio_kelvin);
        radio_kelvin.setText("Kelvin");
        gridBagConstraints = new java.awt.GridBagConstraints();
        gridBagConstraints.gridx = 5;
        gridBagConstraints.gridy = 4;
        gridBagConstraints.gridwidth = 5;
        gridBagConstraints.anchor = java.awt.GridBagConstraints.NORTHWEST;
        gridBagConstraints.insets = new java.awt.Insets(3, 2, 0, 0);
        jPanel1.add(radio_kelvin, gridBagConstraints);

        javax.swing.GroupLayout layout = new javax.swing.GroupLayout(getContentPane());
        getContentPane().setLayout(layout);
        layout.setHorizontalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addComponent(jPanel1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                .addContainerGap())
        );
        layout.setVerticalGroup(
            layout.createParallelGroup(javax.swing.GroupLayout.Alignment.LEADING)
            .addGroup(layout.createSequentialGroup()
                .addContainerGap()
                .addComponent(jPanel1, javax.swing.GroupLayout.DEFAULT_SIZE, javax.swing.GroupLayout.DEFAULT_SIZE, Short.MAX_VALUE)
                .addContainerGap())
        );

        pack();
    }// </editor-fold>                        

    private void txt_suhuKeyTyped(java.awt.event.KeyEvent evt) {                                  
        char input = evt.getKeyChar();
        if (!Character.isDigit(input)) {
            evt.consume();  // Mencegah input selain angka
        }
    }                                 

    /**
     * @param args the command line arguments
     */
    public static void main(String args[]) {
        /* Set the Nimbus look and feel */
        //<editor-fold defaultstate="collapsed" desc=" Look and feel setting code (optional) ">
        /* If Nimbus (introduced in Java SE 6) is not available, stay with the default look and feel.
         * For details see http://download.oracle.com/javase/tutorial/uiswing/lookandfeel/plaf.html 
         */
        try {
            for (javax.swing.UIManager.LookAndFeelInfo info : javax.swing.UIManager.getInstalledLookAndFeels()) {
                if ("Nimbus".equals(info.getName())) {
                    javax.swing.UIManager.setLookAndFeel(info.getClassName());
                    break;
                }
            }
        } catch (ClassNotFoundException ex) {
            java.util.logging.Logger.getLogger(AplikasiKonversiSuhu.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(AplikasiKonversiSuhu.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(AplikasiKonversiSuhu.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(AplikasiKonversiSuhu.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                new AplikasiKonversiSuhu().setVisible(true);
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JButton btn_konversi;
    private javax.swing.ButtonGroup buttonGroup1;
    private javax.swing.JComboBox<String> combo_asal;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JLabel jLabel4;
    private javax.swing.JPanel jPanel1;
    private javax.swing.JRadioButton radio_celcius;
    private javax.swing.JRadioButton radio_fahrenheit;
    private javax.swing.JRadioButton radio_kelvin;
    private javax.swing.JRadioButton radio_reamur;
    private javax.swing.JTextField txt_hasil;
    private javax.swing.JTextField txt_suhu;
    // End of variables declaration                   
}

```
## Authors

Muhammad Hilman (2210010583)
5B Reg Pagi Banjarmasin

## Screenshots
![image](https://github.com/user-attachments/assets/a2d54922-ec4f-4203-ac09-601eb50b2aed)

