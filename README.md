# Android APK Reverse Engineering
### Avengers, Disassemble! 

Neste repositório encontraremos um passo-a-passo de como realizar a Engenharia Reversa de um APK. 

Começando pelo básico, podemos dividir o nosso Android Package (APK) em algumas partes:  
- AndroidManifest.xml 

Composto por todas as permissões que a aplicação vai ter, é responsável por fazer a definição da arquitetura desse apk. Dentro dele encontramos requisição de acesso a internet, GPS, notificações e qualquer outra coisa que o aplicativo venha a necessitar, são geralmente os acessos que o aplicativo pede na hora da instalação. Além disso, encontramos informações voltadas a versionamento, nome da aplicação, requisitos mínimos para que ela funcione, componentes voltados para Receivers, Senders e Providers e componentes 

Abaixo temos um exemplo do que encontramos nesse xml: 

    uses-permission android:name="android.permission.INTERNET" 

    uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" 
    
    uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" 
    
    uses-permission android:name="android.permission.VIBRATE" 
    
    uses-permission android:name="android.permission.WAKE_LOCK" 
    
    uses-permission android:name="com.android.vending.BILLING" 

- META-INF/ 

Essa pasta contém dados relacionados ao Manifest e outros metadatas carregados pelo arquivo .jar.

Dentro dele encontraremos os seguintes arquivos: 

- MANIFEST.MF: versão do pacote, número da compilação, criador, etc. 
- CERT.SF: Nesse doc encontramos a lista de todos os arquivos junto com o resumo do SHA-1.
- CERT.RSA: Aqui temos o conteúdo assinado do arquivo CERT.SF, juntamente com os certificados da chave pública usada para assinatura. 


- classes.dex 

- lib/ 

- assets/ 


### Smali/Baksmali 

O Smali é a versão human readable do Dalvik bytecode, simplificando, funciona como um assemble/disassemble. Dalvik Executable format (.dex)


A termos de código, vamos dar uma olhada na diferença entre Java e Smali:  

    public static void printHelloWorld() {
	System.out.println("Hello World")
    }
    
  E o nosso mesmo código em Smali: 
  
    .method public static printHelloWorld()V
	.registers 2
	sget-object v0, Ljava/lang/System;->out:Ljava/io/PrintStream;
	const-string v1, "Hello World"
	invoke-virtual {v0,v1}, Ljava/io/PrintStream;->println(Ljava/lang/String;)V
	return-void
    .end method

Tools: 
Apktool 


# Dynamic Analysis 



## Tools 

- Mobsf 


# Static Analysis 

- Mobsf 
