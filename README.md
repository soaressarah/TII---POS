# TII---POS
## COMPONENTES
  - Laís Pereira do Nascimento
    - Matrícula: 20141011110107  
    - Github Nickname: laypereirar
  - Sarah Rebecca Soares Penha
    - Matrícula: 20141011110182 
    - Github Nickname: soaressarah  
  - Vanessa Cristiane Santos
    - Matrícula: 20141011110034
    - Github Nickname: santosvanessa
## LINGUAGEM
  - Chakra

## RESUMO
1. Propósito da linguagem
    - Chakra é um código aberto em JavaScript que foi desenvolvido pela Microsoft para a versão do Internet Explorer 9 (32-bit)
2. Paradigma da Linguagem
    - Multi-paradigma
3. Data de criação
    - 2009
4. Principal mantedor
    - Microsoft
## Instalação e Uso
* Instalação
    * O ChakraCore é suportado em Windows 7 ou posterior e Windows Server 2008 R2 ou posterior, com ou [Visual Studio 2013](https://www.microsoft.com/pt-br/download/details.aspx?id=48129) ou [2015](https://www.microsoft.com/en-us/download/details.aspx?id=48146) com suporte de C++ instalados. Após a instalação do Visual Studio:
      1. Clone o ChakraCore através do [link](https://github.com/Microsoft/ChakraCore.git)
      2. Abra Build\Chakra.Core.sln no visual studio
      3. Execute a solução
* Uso
    * Após clonar e instalar o ChakraCore, usuarios de C#, antes de mais nada, precisam adquirir o ChakraCore.dll (Build\VcBuild\bin\[platform+output]\)
    * Para usar o JavaScript Runtime:
      1. Copie ChakraCore.dll para o diretório de saída do projeto.
      2. Em geral, use PInvoke para chamar APIs JSRT. Você pode copiar um wrapper de nossa amostra . Às vezes, pode haver novas APIs que ainda não adicionamos ao wrapper, mas você pode importar do ChakraCore.dll assim:
        <pre>
        [DllImport("ChakraCore.dll")] 
        internal static extern JavaScriptErrorCode JsCreateRuntime(JavaScriptRuntimeAttributes attributes, JavaScriptThreadServiceCallback threadService, out JavaScriptRuntime runtime);
        </pre>
    * Com um projeto novo, inclua o um wrapper C # para JSRT e adicione o CodigoTeste (abaixo) a um arquivo .cs.
    * Compile usando *f6* ou usando Build > Build Solution.
    * Execute a amostra pressionando Ctrl+F5ou usando Debug > Start Without Debugging.
    * <h4>CodigoTeste</h4>
       <pre>
        using System;
        using System.Runtime.InteropServices;
        // wrapper namespace
        using ChakraHost.Hosting;

        public class HelloWorld
        {
        static void Main() {
        JavaScriptRuntime runtime;
        JavaScriptContext context;
        JavaScriptSourceContext currentSourceContext = JavaScriptSourceContext.FromIntPtr(IntPtr.Zero);
        JavaScriptValue result;

        // Your script, try replace the basic hello world with something else
        string script = "(()=>{return \'Hello world!\';})()";

        // Create a runtime. 
        Native.JsCreateRuntime(JavaScriptRuntimeAttributes.None, null, out runtime);
        
        // Create an execution context. 
        Native.JsCreateContext(runtime, out context);
        
        // Now set the execution context as being the current one on this thread.
        Native.JsSetCurrentContext(context);
        
        // Run the script.
        Native.JsRunScript(script, currentSourceContext++, "", out result);

        // Convert your script result to String in JavaScript; redundant if your script returns a String
        JavaScriptValue resultJSString;
        Native.JsConvertValueToString(result, out resultJSString);
        
        // Project script result in JS back to C#.
        IntPtr resultPtr;
        UIntPtr stringLength;
        Native.JsStringToPointer(resultJSString, out resultPtr, out stringLength);

        string resultString = Marshal.PtrToStringUni(resultPtr);
        Console.WriteLine(resultString);
        Console.ReadLine();

        // Dispose runtime
        Native.JsSetCurrentContext(JavaScriptContext.Invalid);
        Native.JsDisposeRuntime(runtime);
        }
        }
        </pre>
## SINTAXE BÁSICA
1. Operadores relacionais e lógicos
   - <b>not</b> : Bool -> Bool <br>
         Nega um valor boleano. 
         <br><br>
            *not True == False* <br>
            *not False == True* <br>
   - <b>(&&)</b> : Bool -> Bool -> Bool <br>
         O operador logico AND. True se ambas entradas forem True.
         <br><br>
        *Note: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é False, não nos incomodamos em avaliar direito e retornar apenas False global.*<br>
   - <b>(||)</b> : Bool -> Bool -> Bool <br>
         O operador logico OR. True se uma ou ambas as entradas forem True.
         <br><br>
        *Note: Quando usado na posição do infixo, como (esquerda && direita), o operador curto-circuita. Isso significa que, se deixado é True, não nos incomodamos em avaliar direito e retornar apenas True global.*<br>
   - <b>xor</b> Bool -> Bool -> Bool <br>
        O operador exlusivo.True se exatamente uma entrada for True.<br>
2. Operadores aritiméticos
