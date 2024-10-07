# Player-Statistics-Caluclator
This program will calculate the average and strike rate of a cricket batsman




import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class PlayerStatisticsCalculator {
    public PlayerStatisticsCalculator() {
        JFrame MyFrame = new JFrame("Player Average and Strike Rate Calculator");
        MyFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        MyFrame.setSize(800, 600); // Increase size for better layout
        MyFrame.setLayout(new BorderLayout());

        JPanel Panel = new JPanel();
        Panel.setLayout(new GridBagLayout());
        Panel.setBackground(Color.gray);

        // GridBagConstraints to position components
        GridBagConstraints gbc = new GridBagConstraints();
        gbc.insets = new Insets(5, 5, 5, 5); // Space between components
        gbc.fill = GridBagConstraints.HORIZONTAL;

        JLabel Heading = new JLabel("Calculate Average and SR of Player");
        Heading.setFont(new Font("Montserrat", Font.BOLD, 24));
        Heading.setForeground(Color.black);
        gbc.gridx = 0; gbc.gridy = 0; gbc.gridwidth = 2; // Heading spans two columns
        Panel.add(Heading, gbc);

        // Labels and text fields
        JLabel Enter_Runs = new JLabel("Enter Runs");
        gbc.gridwidth = 1; // Reset to 1
        gbc.gridx = 0; gbc.gridy = 1;
        Panel.add(Enter_Runs, gbc);

        JTextField Runs = new JTextField(10);
        gbc.gridx = 1; gbc.gridy = 1;
        Panel.add(Runs, gbc);

        JLabel EnterBalls = new JLabel("Enter Balls");
        gbc.gridx = 0; gbc.gridy = 2;
        Panel.add(EnterBalls, gbc);

        JTextField Balls = new JTextField(10);
        gbc.gridx = 1; gbc.gridy = 2;
        Panel.add(Balls, gbc);

        JButton CalculateSR = new JButton("Calculate SR");
        gbc.gridx = 1; gbc.gridy = 3;
        Panel.add(CalculateSR, gbc);

        JLabel ResultOfSR = new JLabel();
        gbc.gridx = 0; gbc.gridy = 4; gbc.gridwidth = 2; // Result spans two columns
        Panel.add(ResultOfSR, gbc);

        JLabel Enter_Runs1 = new JLabel("Enter Runs");
        gbc.gridx = 0; gbc.gridy = 5; gbc.gridwidth = 1;
        Panel.add(Enter_Runs1, gbc);

        JTextField Runs1 = new JTextField(10);
        gbc.gridx = 1; gbc.gridy = 5;
        Panel.add(Runs1, gbc);

        JLabel EnterBalls1 = new JLabel("Enter Outs");
        gbc.gridx = 0; gbc.gridy = 6;
        Panel.add(EnterBalls1, gbc);

        JTextField Out = new JTextField(10);
        gbc.gridx = 1; gbc.gridy = 6;
        Panel.add(Out, gbc);

        JButton CalculateAvg = new JButton("Calculate AVG");
        gbc.gridx = 1; gbc.gridy = 7;
        Panel.add(CalculateAvg, gbc);

        JLabel ResultOfAvg = new JLabel();
        gbc.gridx = 0; gbc.gridy = 8; gbc.gridwidth = 2; // Result spans two columns
        Panel.add(ResultOfAvg, gbc);

        // Action listeners
        CalculateSR.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    float runs = Float.parseFloat(Runs.getText());
                    float balls = Float.parseFloat(Balls.getText());
                    float strikeRate = (runs / balls) * 100;
                    ResultOfSR.setText("SR of Player is : " + String.format("%.2f", strikeRate));
                } catch (NumberFormatException ex) {
                    ResultOfSR.setText("Please enter valid numbers.");
                }
            }
        });

        CalculateAvg.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    float runs1 = Float.parseFloat(Runs1.getText());
                    float out = Float.parseFloat(Out.getText());
                    float average = (out == 0) ? 0 : (runs1 / out); // Prevent division by zero
                    ResultOfAvg.setText("Average of Player is : " + String.format("%.2f", average));
                } catch (NumberFormatException ex) {
                    ResultOfAvg.setText("Please enter valid numbers.");
                }
            }
        });

        MyFrame.add(Panel, BorderLayout.CENTER);
        MyFrame.setVisible(true);
    }

    public static void main(String[] args) {
        new PlayerStatisticsCalculator();
    }
}
