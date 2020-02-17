# ysoserial.net
ysoserial.net for Windows execute file

## Usage

ysoserial.exe -h  
ysoserial.net generates deserialization payloads for a variety of .NET formatters.  

Available gadgets:  

        ActivitySurrogateDisableTypeCheck (Disables 4.8+ type protections for ActivitySurrogateSelector, command is ignored.)  
                Formatters:  
                        BinaryFormatter, LosFormatter, NetDataContractSerializer, ObjectStateFormatter, SoapFormatter  

        ActivitySurrogateSelector (This gadget ignores the command parameter and executes the constructor of ExploitClass class.)  
                Formatters:  
                        BinaryFormatter, LosFormatter, ObjectStateFormatter, SoapFormatter  

        ActivitySurrogateSelectorFromFile (Another variant of the ActivitySurrogateSelector gadget. This gadget interprets the command parameter as path to the .cs file that should be compiled as exploit class. Use semicolon to separate the file from additionally required assemblies, e. g., '-c ExploitClass.cs;System.Windows.Forms.dll'.)  
                Formatters:  
                        BinaryFormatter, LosFormatter, ObjectStateFormatter, SoapFormatter  

        ObjectDataProvider (ObjectDataProvider gadget)  
                Formatters:  
                        DataContractSerializer, FastJson, FsPickler, JavaScriptSerializer, Json.Net, Xaml, XmlSerializer, YamlDotNet < 5.0.0  

        PSObject (PSObject gadget. Target must run a system not patched for CVE-2017-8565 (Published: 07/11/2017))  
                Formatters:  
                        BinaryFormatter, LosFormatter, NetDataContractSerializer, ObjectStateFormatter, SoapFormatter  

        SessionSecurityToken (SessionSecurityTokenGenerator gadget)  
                Formatters:  
                        BinaryFormatter, DataContractSerializer, Json.Net, LosFormatter, NetDataContractSerializer, ObjectStateFormatter, SoapFormatter

        TextFormattingRunProperties (TextFormattingRunProperties gadget)  
                Formatters:  
                        BinaryFormatter, LosFormatter, NetDataContractSerializer, ObjectStateFormatter, SoapFormatter  

        TypeConfuseDelegate (TypeConfuseDelegate gadget)  
                Formatters:  
                        BinaryFormatter, LosFormatter, NetDataContractSerializer, ObjectStateFormatter  

        TypeConfuseDelegateMono (TypeConfuseDelegate gadget - Tweaked to work with Mono)  
                Formatters:  
                        BinaryFormatter, LosFormatter, NetDataContractSerializer, ObjectStateFormatter  

        WindowsClaimsIdentity (WindowsClaimsIdentity (Microsoft.IdentityModel.Claims namespace) gadget)  
                Formatters:  
                        BinaryFormatter, DataContractSerializer, Json.Net, NetDataContractSerializer, SoapFormatter  

        WindowsIdentity (WindowsIdentity gadget)  
                Formatters:  
                        BinaryFormatter, DataContractSerializer, Json.Net, NetDataContractSerializer, SoapFormatter  

Available plugins:  
        ActivatorUrl (Sends a generated payload to an activated, presumably remote, object)  
        Altserialization (Generates payload for HttpStaticObjectsCollection or SessionStateItemCollection)  
        ApplicationTrust (Generates XML payload for the ApplicationTrust class)  
        Clipboard (Generates payload for DataObject and copy it into the clipboard - ready to be pasted in affected apps)  
        DotNetNuke (Generates payload for DotNetNuke CVE-2017-9822)  
        Resx (Generates RESX files)  
        SessionSecurityTokenHandler (Generates XML payload for the SessionSecurityTokenHandler class)  
        SharePoint (Generates poayloads for the following SharePoint CVEs: CVE-2019-0604, CVE-2018-8421)  
        TransactionManagerReenlist (Generates payload for the TransactionManager.Reenlist method)  
        ViewState (Generates a ViewState using known MachineKey parameters)  

Usage: ysoserial.exe [options]  
Options:  
  -p, --plugin=VALUE         The plugin to be used.  
  -o, --output=VALUE         The output format (raw|base64). Default: raw  
  -g, --gadget=VALUE         The gadget chain.  
  -f, --formatter=VALUE      The formatter.  
  -c, --command=VALUE        The command to be executed.  
      --rawcmd               Command will be executed as is without `cmd /c `
                               being appended (anything after first space is an
                               argument).  
  -s, --stdin                The command to be executed will be read from
                               standard input.  
  -t, --test                 Whether to run payload locally. Default: false  
      --minify               Whether to minify the payloads where applicable
                               (experimental). Default: false  
      --sf, --searchformatter=VALUE
                             Search in all formatters to show relevant
                               gadgets and their formatters (other parameters
                               will be ignored).  
  -h, --help                 Shows this message and exit.  
      --credit               Shows the credit/history of gadgets and plugins
                               (other parameters will be ignored).  
