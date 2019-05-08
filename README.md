# Interfaz-Grafica-de-Usuario---El-Ahorcado
Una interfaz grafica de usuario del juego El Ahorcado con base a layouts, botones, imágenes y cajas de texto.

INFORME

PRÁCTICA DE LABORATORIO 

CARRERA: Computación			ASIGNATURA: Programación Aplicada
NRO. PRÁCTICA:	4			TÍTULO PRÁCTICA: Interfaz Gráfica de Usuario (Calculadora, Tres en Raya & El Ahorcado)
OBJETIVO ALCANZADO: Construir interfaces gráficas de usuario
ACTIVIDADES DESARROLLADAS

El Ahorcado
1.	Creación de un repositorio en GitHub:
 
![1](https://user-images.githubusercontent.com/49033904/57345047-2292b980-710f-11e9-9a86-b9bd6f7e10c2.png)

Link: https://github.com/DomenikaD/Interfaz-Grafica-de-Usuario---El-Ahorcado

Usuario: DomenikaD

2.	Commits:
 

![2](https://user-images.githubusercontent.com/49033904/57345048-2292b980-710f-11e9-87a2-0b71a7c12f19.png)


3.	Paquete imagen & vista:


![3](https://user-images.githubusercontent.com/49033904/57345049-2292b980-710f-11e9-9585-dab1fc35a372.png)
 
4.	Código
Paquete Imagen

![1](https://user-images.githubusercontent.com/49033904/57345117-4eae3a80-710f-11e9-956f-d895f729e8b8.png)
![2](https://user-images.githubusercontent.com/49033904/57345118-4eae3a80-710f-11e9-9118-304a6ab9d352.png)
![3](https://user-images.githubusercontent.com/49033904/57345119-4eae3a80-710f-11e9-8095-89b1ec2a1b5d.png)
![4](https://user-images.githubusercontent.com/49033904/57345120-4eae3a80-710f-11e9-9739-b59007bf28ec.png)
![5](https://user-images.githubusercontent.com/49033904/57345121-4eae3a80-710f-11e9-81a4-741310a9ea98.png)
![6](https://user-images.githubusercontent.com/49033904/57345122-4f46d100-710f-11e9-8166-814f785afae4.png)

     

JFrame Ventana Principal

package ec.edu.ups.vista;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.image.BufferedImage;
import java.io.IOException;
import java.net.URL;
import java.util.logging.Level;
import java.util.logging.Logger;
import javax.imageio.ImageIO;
import javax.swing.ImageIcon;
import javax.swing.JButton;
import javax.swing.JOptionPane;

/**
 *
 * @author Domenika Delgado
 */
public class VentanaPrincipal extends javax.swing.JFrame {
    
    
    public ImageIcon imI[];
    public JButton btt[];
    public String palabra[];
    public int alea;
    public int error;
    public String respuesta[];

    public VentanaPrincipal()throws IOException {
        initComponents();
        
        //Posicion de la ventana 
        this.setLocationRelativeTo(null);
        
        
        imI = new ImageIcon[6];
        btt = new JButton[27];
        palabra = new String[10];

        //Imagenes del ahorcado
        imI[0] = new ImageIcon("src/ec/edu/ups/imagen/1.png");       
        imI[1] = new ImageIcon("src/ec/edu/ups/imagen/2.png");
        imI[2] = new ImageIcon("src/ec/edu/ups/imagen/3.png");
        imI[3] = new ImageIcon("src/ec/edu/ups/imagen/4.png");
        imI[4] = new ImageIcon("src/ec/edu/ups/imagen/5.png");
        imI[5] = new ImageIcon("src/ec/edu/ups/imagen/6.png");

        //Botones de las letras
        btt[1] = jButton2;
        btt[2] = jButton3;
        btt[3] = jButton4;
        btt[4] = jButton5;
        btt[5] = jButton6;
        btt[6] = jButton7;
        btt[7] = jButton8;
        btt[8] = jButton9;
        btt[9] = jButton10;
        btt[10] = jButton11;
        btt[11] = jButton12;
        btt[12] = jButton13;
        btt[13] = jButton14;
        btt[14] = jButton15;
        btt[15] = jButton16;
        btt[16] = jButton17;
        btt[17] = jButton18;
        btt[18] = jButton19;
        btt[19] = jButton20;
        btt[20] = jButton21;
        btt[21] = jButton22;
        btt[22] = jButton23;
        btt[23] = jButton24;
        btt[24] = jButton25;
        btt[25] = jButton26;
        btt[26] = jButton27;

        //Palabras (Diccionario)
        palabra[0] = "elefante".toUpperCase();
        palabra[1] = "tigre".toUpperCase();
        palabra[2] = "futbol".toUpperCase();
        palabra[3] = "volley".toUpperCase();
        palabra[4] = "manzana".toUpperCase();
        palabra[5] = "fresa".toUpperCase();
        palabra[6] = "morado".toUpperCase();
        palabra[7] = "verde".toUpperCase();
        palabra[8] = "computacion".toUpperCase();
        palabra[9] = "medicina".toUpperCase();
       
        
      

        //Se asigna un evento a cada letra para comprobar que exista en la palabra 
        for (int i = 1; i < 27; i++) {
            btt[i].addActionListener(new ActionListener() {
                public void actionPerformed(ActionEvent e) {
                    checarLetra(e);
                }
            });
        }
        iniciar();
    }

    //Comenzar los parametros del juego o si se inicio un nuevo juego
    public void iniciar() {
        error = 0;
        jButton1.setIcon(imI[0]);
        jTextPane1.setText("");
        //para activar las letras del tablero
        for (int i = 1; i < 27; i++) {
            btt[i].setEnabled(true);
        }
        //Para generar una palabra aleatoriamente 
        alea = (int) 0 + (int) (Math.random() * ((palabra.length - 1) + 1));
        
        
        
        //Separar
        String pal[] = palabra[alea].split(" ");
        respuesta = new String[palabra[alea].length() + 1];
        int j = 0;
        
        //Se pone los guiones que van debajo de las letras como una separacion (_)
        for (String pal1 : pal) {
            for (int i = 0; i < pal1.length(); i++) {
                jTextPane1.setText(jTextPane1.getText() + "_ ");
                respuesta[j++] = "_";
            }
            jTextPane1.setText(jTextPane1.getText() + "\n");
            respuesta[j++] = " ";
        }
        
        if(alea==0 || alea ==1){
            jLabel3.setText("");
            jLabel3.setText("Animales");
        }else if(alea==2 || alea ==3){
            jLabel3.setText("");
            jLabel3.setText("Deportes");
        }else if(alea==4 || alea ==5){
            jLabel3.setText("");
            jLabel3.setText("Frutas");
        }else if(alea==6 || alea ==7){
            jLabel3.setText("");
            jLabel3.setText("Colores");
        }else if(alea==8 || alea ==9){
            jLabel3.setText("");
            jLabel3.setText("Carreras");
        }
    }

    //Presionar una letra, se busca si pertenece a la palabra sino lo marca como error 
    public void checarLetra(ActionEvent e) {
        JButton bt = (JButton) e.getSource();
        char c[];
        
        //Busca la letra 
        for (int i = 1; i < 27; i++) {
            if (bt == btt[i]) {
                
                c = Character.toChars(64 + i);
                //Busca si la letra valorVerd 
                boolean valorVerd = false;
                for (int j = 0; j < palabra[alea].length(); j++) {
                    if (c[0] == palabra[alea].charAt(j)) {
                        respuesta[j] = c[0] + "";
                        valorVerd = true;
                    }
                }
                //Si existe la letra se muestra en el JFrame
                if (valorVerd) {
                    jTextPane1.setText("");
                    for (String re : respuesta) {
                        if (" ".equals(re)) {
                            jTextPane1.setText(jTextPane1.getText() + "\n");
                        } else {
                            jTextPane1.setText(jTextPane1.getText() + re + " ");
                        }
                    }
                    //Comprobacion si la palabra esta completa
                    boolean gano = true;
                    for (String re : respuesta) {
                        if (re.equals("_")) {
                            gano = false;
                            break;
                        }
                    }
                    //Si esta correcta, se muestra mensaje
                    if (gano) {
                        JOptionPane.showMessageDialog(this, "***Advino la Palabra***");
                        iniciar();
                        return;
                    }
                    //Suma de Errores
                } else {
                    jButton1.setIcon(imI[++error]);
                    //Si llega a los error permitidos(5), el juego comienza de nuevo
                    if (error == 5) {
                        JOptionPane.showMessageDialog(this, "Intente de Nuevo :(  \n" + palabra[alea]);
                        iniciar();
                        return;
                    }
                }
                //valorVerd: Desactiva las letras ya seleccionadas 
                bt.setEnabled(false);
                break;
            }
        }

    }

    /**
     * Creates new form VentanaPrincipal
     */
 

    /**
     * This method is called from within the constructor to initialize the form.
     * WARNING: Do NOT modify this code. The content of this method is always
     * regenerated by the Form Editor.
     */
    @SuppressWarnings("unchecked")
    // <editor-fold defaultstate="collapsed" desc="Generated Code">                          
    private void initComponents() {

        jButton12 = new javax.swing.JButton();
        jButton5 = new javax.swing.JButton();
        jButton6 = new javax.swing.JButton();
        jButton13 = new javax.swing.JButton();
        jButton20 = new javax.swing.JButton();
        jButton28 = new javax.swing.JButton();
        jButton26 = new javax.swing.JButton();
        jScrollPane1 = new javax.swing.JScrollPane();
        jTextPane1 = new javax.swing.JTextPane();
        jButton27 = new javax.swing.JButton();
        jButton21 = new javax.swing.JButton();
        jButton22 = new javax.swing.JButton();
        jButton2 = new javax.swing.JButton();
        jButton15 = new javax.swing.JButton();
        jButton9 = new javax.swing.JButton();
        jButton7 = new javax.swing.JButton();
        jButton16 = new javax.swing.JButton();
        jButton8 = new javax.swing.JButton();
        jButton17 = new javax.swing.JButton();
        jButton14 = new javax.swing.JButton();
        jButton10 = new javax.swing.JButton();
        jButton3 = new javax.swing.JButton();
        jButton11 = new javax.swing.JButton();
        jButton4 = new javax.swing.JButton();
        jButton18 = new javax.swing.JButton();
        jButton23 = new javax.swing.JButton();
        jButton24 = new javax.swing.JButton();
        jButton25 = new javax.swing.JButton();
        jButton19 = new javax.swing.JButton();
        jLabel1 = new javax.swing.JLabel();
        jButton1 = new javax.swing.JButton();
        jLabel2 = new javax.swing.JLabel();
        jLabel3 = new javax.swing.JLabel();

        setDefaultCloseOperation(javax.swing.WindowConstants.EXIT_ON_CLOSE);
        getContentPane().setLayout(new org.netbeans.lib.awtextra.AbsoluteLayout());

        jButton12.setBackground(new java.awt.Color(255, 255, 255));
        jButton12.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton12.setText("K");
        getContentPane().add(jButton12, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 260, -1, -1));

        jButton5.setBackground(new java.awt.Color(255, 255, 255));
        jButton5.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton5.setText("D");
        getContentPane().add(jButton5, new org.netbeans.lib.awtextra.AbsoluteConstraints(650, 180, -1, -1));

        jButton6.setBackground(new java.awt.Color(255, 255, 255));
        jButton6.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton6.setText("E");
        getContentPane().add(jButton6, new org.netbeans.lib.awtextra.AbsoluteConstraints(700, 180, -1, -1));

        jButton13.setBackground(new java.awt.Color(255, 255, 255));
        jButton13.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton13.setText("L");
        getContentPane().add(jButton13, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 260, -1, -1));

        jButton20.setBackground(new java.awt.Color(255, 255, 255));
        jButton20.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton20.setText("S");
        getContentPane().add(jButton20, new org.netbeans.lib.awtextra.AbsoluteConstraints(650, 300, -1, -1));

        jButton28.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton28.setText("Reiniciar");
        jButton28.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton28ActionPerformed(evt);
            }
        });
        getContentPane().add(jButton28, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 430, 177, 57));

        jButton26.setBackground(new java.awt.Color(255, 255, 255));
        jButton26.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton26.setText("Y");
        getContentPane().add(jButton26, new org.netbeans.lib.awtextra.AbsoluteConstraints(700, 340, -1, -1));

        jTextPane1.setEditable(false);
        jTextPane1.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jScrollPane1.setViewportView(jTextPane1);

        getContentPane().add(jScrollPane1, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 100, 260, 60));

        jButton27.setBackground(new java.awt.Color(255, 255, 255));
        jButton27.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton27.setText("Z");
        getContentPane().add(jButton27, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 380, -1, -1));

        jButton21.setBackground(new java.awt.Color(255, 255, 255));
        jButton21.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton21.setText("T");
        getContentPane().add(jButton21, new org.netbeans.lib.awtextra.AbsoluteConstraints(700, 300, -1, -1));

        jButton22.setBackground(new java.awt.Color(255, 255, 255));
        jButton22.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton22.setText("U");
        getContentPane().add(jButton22, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 340, -1, -1));

        jButton2.setBackground(new java.awt.Color(255, 255, 255));
        jButton2.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton2.setText("A");
        jButton2.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton2ActionPerformed(evt);
            }
        });
        getContentPane().add(jButton2, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 180, -1, -1));

        jButton15.setBackground(new java.awt.Color(255, 255, 255));
        jButton15.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton15.setText("N");
        getContentPane().add(jButton15, new org.netbeans.lib.awtextra.AbsoluteConstraints(650, 260, -1, -1));

        jButton9.setBackground(new java.awt.Color(255, 255, 255));
        jButton9.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton9.setText("H");
        getContentPane().add(jButton9, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 220, -1, -1));

        jButton7.setBackground(new java.awt.Color(255, 255, 255));
        jButton7.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton7.setText("F");
        getContentPane().add(jButton7, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 220, -1, -1));

        jButton16.setBackground(new java.awt.Color(255, 255, 255));
        jButton16.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton16.setText("O");
        getContentPane().add(jButton16, new org.netbeans.lib.awtextra.AbsoluteConstraints(700, 260, -1, -1));

        jButton8.setBackground(new java.awt.Color(255, 255, 255));
        jButton8.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton8.setText("G");
        getContentPane().add(jButton8, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 220, -1, -1));

        jButton17.setBackground(new java.awt.Color(255, 255, 255));
        jButton17.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton17.setText("P");
        getContentPane().add(jButton17, new org.netbeans.lib.awtextra.AbsoluteConstraints(500, 300, -1, -1));

        jButton14.setBackground(new java.awt.Color(255, 255, 255));
        jButton14.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton14.setText("M");
        getContentPane().add(jButton14, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 260, -1, -1));

        jButton10.setBackground(new java.awt.Color(255, 255, 255));
        jButton10.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton10.setText("I");
        getContentPane().add(jButton10, new org.netbeans.lib.awtextra.AbsoluteConstraints(650, 220, -1, -1));

        jButton3.setBackground(new java.awt.Color(255, 255, 255));
        jButton3.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton3.setText("B");
        getContentPane().add(jButton3, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 180, -1, -1));

        jButton11.setBackground(new java.awt.Color(255, 255, 255));
        jButton11.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton11.setText("J");
        jButton11.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton11ActionPerformed(evt);
            }
        });
        getContentPane().add(jButton11, new org.netbeans.lib.awtextra.AbsoluteConstraints(700, 220, -1, -1));

        jButton4.setBackground(new java.awt.Color(255, 255, 255));
        jButton4.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton4.setText("C");
        getContentPane().add(jButton4, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 180, -1, -1));

        jButton18.setBackground(new java.awt.Color(255, 255, 255));
        jButton18.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton18.setText("Q");
        getContentPane().add(jButton18, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 300, -1, -1));

        jButton23.setBackground(new java.awt.Color(255, 255, 255));
        jButton23.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton23.setText("V");
        getContentPane().add(jButton23, new org.netbeans.lib.awtextra.AbsoluteConstraints(550, 340, -1, -1));

        jButton24.setBackground(new java.awt.Color(255, 255, 255));
        jButton24.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton24.setText("W");
        getContentPane().add(jButton24, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 340, -1, -1));

        jButton25.setBackground(new java.awt.Color(255, 255, 255));
        jButton25.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton25.setText("X");
        getContentPane().add(jButton25, new org.netbeans.lib.awtextra.AbsoluteConstraints(650, 340, -1, -1));

        jButton19.setBackground(new java.awt.Color(255, 255, 255));
        jButton19.setFont(new java.awt.Font("Consolas", 0, 18)); // NOI18N
        jButton19.setText("R");
        getContentPane().add(jButton19, new org.netbeans.lib.awtextra.AbsoluteConstraints(600, 300, -1, -1));

        jLabel1.setBackground(new java.awt.Color(255, 255, 51));
        jLabel1.setFont(new java.awt.Font("Times New Roman", 1, 36)); // NOI18N
        jLabel1.setForeground(new java.awt.Color(255, 0, 0));
        jLabel1.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel1.setText("El Ahorcado");
        jLabel1.setBorder(javax.swing.BorderFactory.createMatteBorder(1, 1, 1, 1, new java.awt.Color(153, 255, 51)));
        getContentPane().add(jLabel1, new org.netbeans.lib.awtextra.AbsoluteConstraints(210, 10, 380, 40));

        jButton1.addActionListener(new java.awt.event.ActionListener() {
            public void actionPerformed(java.awt.event.ActionEvent evt) {
                jButton1ActionPerformed(evt);
            }
        });
        getContentPane().add(jButton1, new org.netbeans.lib.awtextra.AbsoluteConstraints(50, 80, 350, 360));

        jLabel2.setFont(new java.awt.Font("Times New Roman", 1, 18)); // NOI18N
        jLabel2.setForeground(new java.awt.Color(0, 153, 153));
        jLabel2.setHorizontalAlignment(javax.swing.SwingConstants.CENTER);
        jLabel2.setText("Pista:");
        getContentPane().add(jLabel2, new org.netbeans.lib.awtextra.AbsoluteConstraints(70, 460, 60, 20));
        getContentPane().add(jLabel3, new org.netbeans.lib.awtextra.AbsoluteConstraints(130, 450, 170, 40));

        pack();
    }// </editor-fold>                        

    private void jButton28ActionPerformed(java.awt.event.ActionEvent evt) {                                          
        iniciar();
    }                                         

    private void jButton2ActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
    }                                        

    private void jButton11ActionPerformed(java.awt.event.ActionEvent evt) {                                          
        // TODO add your handling code here:
    }                                         

    private void jButton1ActionPerformed(java.awt.event.ActionEvent evt) {                                         
        // TODO add your handling code here:
        
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
            java.util.logging.Logger.getLogger(VentanaPrincipal.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (InstantiationException ex) {
            java.util.logging.Logger.getLogger(VentanaPrincipal.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (IllegalAccessException ex) {
            java.util.logging.Logger.getLogger(VentanaPrincipal.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        } catch (javax.swing.UnsupportedLookAndFeelException ex) {
            java.util.logging.Logger.getLogger(VentanaPrincipal.class.getName()).log(java.util.logging.Level.SEVERE, null, ex);
        }
        //</editor-fold>

        /* Create and display the form */
        java.awt.EventQueue.invokeLater(new Runnable() {
            public void run() {
                try {
                    new VentanaPrincipal().setVisible(true);
                } catch (IOException ex) {
                    Logger.getLogger(VentanaPrincipal.class.getName()).log(Level.SEVERE, null, ex);
                }
            }
        });
    }

    // Variables declaration - do not modify                     
    private javax.swing.JButton jButton1;
    private javax.swing.JButton jButton10;
    private javax.swing.JButton jButton11;
    private javax.swing.JButton jButton12;
    private javax.swing.JButton jButton13;
    private javax.swing.JButton jButton14;
    private javax.swing.JButton jButton15;
    private javax.swing.JButton jButton16;
    private javax.swing.JButton jButton17;
    private javax.swing.JButton jButton18;
    private javax.swing.JButton jButton19;
    private javax.swing.JButton jButton2;
    private javax.swing.JButton jButton20;
    private javax.swing.JButton jButton21;
    private javax.swing.JButton jButton22;
    private javax.swing.JButton jButton23;
    private javax.swing.JButton jButton24;
    private javax.swing.JButton jButton25;
    private javax.swing.JButton jButton26;
    private javax.swing.JButton jButton27;
    private javax.swing.JButton jButton28;
    private javax.swing.JButton jButton3;
    private javax.swing.JButton jButton4;
    private javax.swing.JButton jButton5;
    private javax.swing.JButton jButton6;
    private javax.swing.JButton jButton7;
    private javax.swing.JButton jButton8;
    private javax.swing.JButton jButton9;
    private javax.swing.JLabel jLabel1;
    private javax.swing.JLabel jLabel2;
    private javax.swing.JLabel jLabel3;
    private javax.swing.JScrollPane jScrollPane1;
    private javax.swing.JTextPane jTextPane1;
    // End of variables declaration                   
}

5.	Diseño:


![4](https://user-images.githubusercontent.com/49033904/57345050-2292b980-710f-11e9-9826-f219189220a2.png)
 

6.	Funcionamiento:


![5](https://user-images.githubusercontent.com/49033904/57345052-232b5000-710f-11e9-8064-ecd370b07f90.png)
 
Ejemplo:


![6](https://user-images.githubusercontent.com/49033904/57345053-232b5000-710f-11e9-987b-56f70a48c3e7.png)


![7](https://user-images.githubusercontent.com/49033904/57345054-232b5000-710f-11e9-8aa4-ba18d3d61fc6.png)

 
7.	Explicación del funcionamiento de la Interfaz gráfica de usuario – El Ahorcado:
Este proyecto es sobre el juego El Ahorcado, lo cual se encuentra el lenguaje de programación de Java. El juego tiene 5 temas, lo cuales se da una pista para poder adivinar la palabra.


RESULTADO(S) OBTENIDO(S):

Las Interfaces Graficas de Usuario

     El Ahorcado
     
![5](https://user-images.githubusercontent.com/49033904/57345052-232b5000-710f-11e9-8064-ecd370b07f90.png)


CONCLUSIONES: Podemos llegar a realizar diferentes interfaces utilizando código que nos puede generar Netbeans, de esto se puede entender el funcionamiento de casa cosa & tener en cuenta que un arreglo puede ser muy útil al rato de crear juegos, como por ejemplo: Tres en Raya & El Ahorcado. 


RECOMENDACIONES: Tener en cuenta la implementación con base de layouts, los botones y cajas de texto que nos permite realizar en un JFrame  y tener como resultado el código Generadotra. Ejemplo: La calculadora.


Nombre de estudiante: Domenika Delgado


Firma de estudiante:  ![8](https://user-images.githubusercontent.com/49033904/57277951-d857fc80-706a-11e9-9b3e-f022b2245bbe.jpg)



