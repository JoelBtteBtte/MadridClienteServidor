# MadridClienteServidor
Programa de interacción entre usuarios

import java.io.*;
import java.net.*;

class Cliente {

    static final String HOST = "localhost";//Dirección del Servidor
    static final int PUERTO=4545;

    public Cliente() {

        String  teclaCadena= "";
        String receptorDatos ="";

        Scanner teclado = new Scanner(System.in);

        try{

            Socket skCliente = new Socket( HOST , PUERTO );

            InputStream aux = skCliente.getInputStream();
            OutputStream auxSalida = skCliente.getOutputStream();

            DataInputStream flujo = new DataInputStream( aux );
            DataOutputStream salida = new DataOutputStream( auxSalida );

           receptorDatos= flujo.readUTF();
           System.out.println("Servidor: " + receptorDatos);

           System.out.print("Accion a realizar:"); teclaCadena = teclado.read();
          
          salida.writeUTF(teclaCadena);//Trasmisión de Datos
          skCliente.close();

        } catch( Exception e ) {
          System.out.println(e);
        }

    }

    public static void main( String[] arg ) {
        new Cliente();
    }
  }  
  
  
