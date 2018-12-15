# Start Metamap Server in Java
-------------------------
[Metamap](https://metamap.nlm.nih.gov/) is a tool to recognize UMLS concepts in text. Here is a short script of Java for starting Metamap server. 
For details of installation of Metamap Java Api, please check [here](https://gist.github.com/patrick013/32a85a40402654ba6417e4dab4a98c98).

```javascript
import java.awt.Desktop;
import java.io.BufferedReader;
import java.io.File;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.concurrent.TimeUnit;
 
public class ServerStart {
	
	public static void main(String args[]) throws IOException {
		new ServerStart();
	}
	
	public ServerStart() throws IOException {		
		//Check If the MetaMap server is running in the process
		String line;
		String pidInfo ="";

		Process p =Runtime.getRuntime().exec(System.getenv("windir") +"\\system32\\"+"tasklist.exe");

		BufferedReader input =  new BufferedReader(new InputStreamReader(p.getInputStream()));

		while ((line = input.readLine()) != null) {
		    pidInfo+=line; 
		}

		input.close();

		//Start the MetaMap Server
		if(!pidInfo.contains("mmserver14"))
		{
		    Desktop.getDesktop().open(new File("R:\\Metamap\\public_mm\\bin\\skrmedpostctl_start.bat"));
		    Desktop.getDesktop().open(new File("R:\\Metamap\\public_mm\\bin\\wsdserverctl_start.bat"));
		    Desktop.getDesktop().open(new File("R:\\Metamap\\public_mm\\bin\\mmserver14.bat"));	
		}

	}
	public static void ServerCheck() throws IOException, InterruptedException {		
		//Check If the MetaMap server is running in the process
		String line;
		String pidInfo ="";

		Process p =Runtime.getRuntime().exec(System.getenv("windir") +"\\system32\\"+"tasklist.exe");

		BufferedReader input =  new BufferedReader(new InputStreamReader(p.getInputStream()));

		while ((line = input.readLine()) != null) {
		    pidInfo+=line; 
		}

		input.close();

		//Start the MetaMap Server
		if(!pidInfo.contains("mmserver14"))
		{
		    Desktop.getDesktop().open(new File("R:\\Metamap\\public_mm\\bin\\mmserver14.bat"));	
		    TimeUnit.SECONDS.sleep(10);
		}

	}
}
```
