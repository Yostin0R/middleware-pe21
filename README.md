PS D:\Universidad\Programacion Middleware\middleware-pe21> # (a) Sin API key -> esperado: 401
>> curl http://localhost:3000/health
>> 
curl : {"error":"API key inválida o ausente"}
En línea: 2 Carácter: 1
+ curl http://localhost:3000/health
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation:  
   (System.Net.HttpWebRequest:HttpWebRequest) [  
  Invoke-WebRequest], WebException
    + FullyQualifiedErrorId : WebCmdletWebRespon 
   seException,Microsoft.PowerShell.Commands.In  
  vokeWebRequestCommand
PS D:\Universidad\Programacion Middleware\middleware-pe21> # (b) Con clave válida -> esperado: 200
>> curl -H "x-api-key: secreto-demo" http://localhost:3000/health
>> 
Invoke-WebRequest : No se puede enlazar el 
parámetro 'Headers'. No se puede convertir el 
valor "x-api-key: secreto-demo" de tipo 
"System.String" al tipo 
"System.Collections.IDictionary".
En línea: 2 Carácter: 9
+ curl -H "x-api-key: secreto-demo" 
http://localhost:3000/health
+         ~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: ( 
   :) [Invoke-WebRequest], ParameterBindingExce  
  ption
    + FullyQualifiedErrorId : CannotConvertArgum 
   entNoMessage,Microsoft.PowerShell.Commands.I  
  nvokeWebRequestCommand
 
PS D:\Universidad\Programacion Middleware\middleware-pe21> # (c) Ruta inexistente -> esperado: 404
>> curl -H "x-api-key: secreto-demo" http://localhost:3000/noexiste
>> 
Invoke-WebRequest : No se puede enlazar el 
parámetro 'Headers'. No se puede convertir el 
valor "x-api-key: secreto-demo" de tipo 
"System.String" al tipo 
"System.Collections.IDictionary".
En línea: 2 Carácter: 9
+ curl -H "x-api-key: secreto-demo" 
http://localhost:3000/noexiste
+         ~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: ( 
   :) [Invoke-WebRequest], ParameterBindingExce  
  ption
    + FullyQualifiedErrorId : CannotConvertArgum 
   entNoMessage,Microsoft.PowerShell.Commands.I  
  nvokeWebRequestCommand
 
PS D:\Universidad\Programacion Middleware\middleware-pe21> 