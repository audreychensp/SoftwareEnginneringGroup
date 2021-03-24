# StudentChat
Chat Function from Students perspective

/* This code runs to show a chat inbox feature. This is the student's point of view. 
The message sent from this compiler appears in the teaching assistant's compiler and vice versa. */

import java.net.*;
import java.io.*;

class Student{
	public static void main(String[] args) {
		try{ 

			ServerSocket ss = new ServerSocket(1201);
			Socket s = ss.accept();

			DataInputStream din = new DataInputStream(s.getInputStream()); 
			DataOutputStream dout = new DataOutputStream(s.getOutputStream());

			BufferedReader br = new BufferedReader(new InputStreamReader(System.in));

			String msgin="",msgout="";

			while(!msgin.equals("end")){
				msgin = din.readUTF();
				System.out.println(msgin);
				msgout = br.readLine();
				dout.writeUTF(msgout);
				dout.flush();

			}
			s.close();

		}catch(Exception e){

		}
	}
}



