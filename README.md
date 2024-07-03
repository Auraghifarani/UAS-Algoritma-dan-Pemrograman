# UAS-Algoritma-dan-Pemrograman
## PROGRAM MENGHITUNG ONGKOS OJEK ONLINE
## AURA GHIFARANI (1237050145)
import javax.swing.*;
import javax.swing.text.AttributeSet.FontAttribute;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class HitungBiayaOjekOnline extends JFrame {
    private JTextField jarakField;
    private JTextField waktuField;
    private JComboBox<String> layananComboBox;
    private JLabel resultLabel;

    public HitungBiayaOjekOnline() {
        setTitle("Program Penghitung Biaya Ojek Online Aura");
        setSize(500, 500);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new GridLayout(5, 2));

        JLabel jarakLabel = new JLabel("Masukkan jarak tempuh (dalam KM):");
        jarakField = new JTextField();

        JLabel waktuLabel = new JLabel("Masukkan waktu tempuh (dalam menit):");
        waktuField = new JTextField();

        JLabel layananLabel = new JLabel("Pilih jenis layanan (standar/premium):");
        layananComboBox = new JComboBox<>(new String[]{"standar", "premium"});

        JButton hitungButton = new JButton("Hitung Biaya");
        hitungButton.addActionListener(new HitungButtonListener());

        resultLabel = new JLabel("Total Biaya: Rp 0");

        add(jarakLabel);
        add(jarakField);
        add(waktuLabel);
        add(waktuField);
        add(layananLabel);
        add(layananComboBox);
        add(hitungButton);
        add(resultLabel);
    }

    private class HitungButtonListener implements ActionListener {
        @Override
        public void actionPerformed(ActionEvent e) {
            try {
                double jarakTempuh = Double.parseDouble(jarakField.getText());
                double waktuTempuh = Double.parseDouble(waktuField.getText());
                String jenisLayanan = (String) layananComboBox.getSelectedItem();

                int tarifDasar = 7000;
                float tarifPerKm = 5000;
                int tarifPerMenit = 1000;
                int tarifPremiumPerKm = 3000;
                int tarifPremiumPerMenit = 1500;

                double biaya;
                if ("premium".equalsIgnoreCase(jenisLayanan)) {
                    biaya = tarifDasar + (jarakTempuh * tarifPremiumPerKm) + (waktuTempuh * tarifPremiumPerMenit);
                } else {
                    biaya = tarifDasar + (jarakTempuh * tarifPerKm) + (waktuTempuh * tarifPerMenit);
                }

                resultLabel.setText("Total Biaya: Rp " + biaya);
            } catch (NumberFormatException ex) {
                JOptionPane.showMessageDialog(HitungBiayaOjekOnline.this, "Input tidak valid. Masukkan angka yang benar.", "Error", JOptionPane.ERROR_MESSAGE);
            }
        }
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(() -> {
            HitungBiayaOjekOnline frame = new HitungBiayaOjekOnline();
            frame.setVisible(true);
        });
    }
}
![image](https://github.com/Auraghifarani/UAS-Algoritma-dan-Pemrograman/assets/144779697/550444c6-b7e0-4930-a949-e56fc868f71d)
![image](https://github.com/Auraghifarani/UAS-Algoritma-dan-Pemrograman/assets/144779697/709d724b-a1c8-448b-af0b-961ee9a8badd)

