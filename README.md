package vistas;

import java.awt.event.KeyAdapter;
import java.awt.event.KeyEvent;
import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JPasswordField;
import javax.swing.JTextField;

public class PantallaLogin {

    public JFrame ventanaLogin;
    //botones
    public JButton btnCancelar, btnIniciar, btnRecuperarSesion;
    //cuadro de texto
    public JTextField txtIdUsu;
    //etiqueta
    public JLabel etiNomUsu, etiContra, etiImagen, etiTitulo;
    //pass word
    public JPasswordField txtContra;
    //imagenes
    public ImageIcon imagen;

    public PantallaLogin() {

        ventanaLogin = new JFrame();
        ventanaLogin.setTitle("LOGIN");

        etiTitulo = new JLabel("SISTEMA DE ADMINISTRACION DE HISTORIAS CLINICAS");
        etiTitulo.setBounds(150, 30, 330, 50);
        ventanaLogin.add(etiTitulo);

        //imagen de fondo
        imagen = new ImageIcon("C:\\Users\\MariDavid\\Documents\\NetBeansProjects\\HISTORIASCLINICAS\\src\\imagenes\\adminis.jpg");
        etiImagen = new JLabel(imagen);
        etiImagen.setBounds(200, 70, 200, 200);
        ventanaLogin.add(etiImagen);

        etiNomUsu = new JLabel("Usuario");
        etiNomUsu.setBounds(130, 280, 200, 30);
        ventanaLogin.add(etiNomUsu);

        txtIdUsu = new JTextField();
        txtIdUsu.setBounds(200, 280, 200, 30);
        ventanaLogin.add(txtIdUsu);

        etiContra = new JLabel("Contraseña");
        etiContra.setBounds(130, 330, 200, 30);
        ventanaLogin.add(etiContra);

        txtContra = new JPasswordField(10);
        txtContra.setBounds(200, 330, 200, 30);
        ventanaLogin.add(txtContra);

        btnIniciar = new JButton("Iniciar");
        btnIniciar.setBounds(200, 370, 200, 30);
        ventanaLogin.add(btnIniciar);

        btnRecuperarSesion = new JButton("Recuperar Contraseña");
        btnRecuperarSesion.setBounds(200, 410, 200, 30);
        ventanaLogin.add(btnRecuperarSesion);

        btnCancelar = new JButton("Cancelar");
        btnCancelar.setBounds(200, 450, 200, 30);
        ventanaLogin.add(btnCancelar);

        ventanaLogin.setSize(600, 600);
        ventanaLogin.setLayout(null);
        ventanaLogin.setResizable(false);
        ventanaLogin.setDefaultCloseOperation(3);
        ventanaLogin.setVisible(true);
        txtIdUsu.setFocusable(true);

        snumeros(txtIdUsu);
        limitar();
    }

    public void limitar() {
        txtContra.setDocument(new LimitarCaracter(txtContra, 44));
        txtIdUsu.setDocument(new LimitarCaracter(txtIdUsu, 8));
    }

    public void sletras(JTextField a) { //el q vamos a usar 
        a.addKeyListener(new KeyAdapter() {
            public void keyTyped(KeyEvent e) {
                char c = e.getKeyChar();
                if (!Character.isLetter(c) && !Character.isSpaceChar(c)) {
                    ventanaLogin.getToolkit().beep();
                    e.consume();//no permite ingresr numero
                }}});}

    public void snumeros(JTextField a) { // el tipo dobjeto que vamos a usar + una variable 
        a.addKeyListener(new KeyAdapter() {
            public void keyTyped(KeyEvent e) {
                char c = e.getKeyChar();//variable que estemos ingresando
                if (!Character.isDigit(c)) {
                    ventanaLogin.getToolkit().beep();
                    e.consume();//no permite ingresar letras
                }}});}

    public static void main(String[] args) {
        PantallaLogin mostrar = new PantallaLogin();
    }
}

