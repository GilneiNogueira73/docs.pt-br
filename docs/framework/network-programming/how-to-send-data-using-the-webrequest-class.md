---
title: Como enviar dados usando a classe WebRequest
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WebRequest class, sending data to a host
- Sending data to a host, using WebRequest class
ms.assetid: 66686878-38ac-4aa6-bf42-ffb568ffc459
caps.latest.revision: 12
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c840792182c012ba74b3ba3ef297748f58e4b92a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-send-data-using-the-webrequest-class"></a><span data-ttu-id="5a679-102">Como enviar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="5a679-102">How to: Send Data Using the WebRequest Class</span></span>
<span data-ttu-id="5a679-103">O procedimento a seguir descreve as etapas usadas para enviar dados para um servidor.</span><span class="sxs-lookup"><span data-stu-id="5a679-103">The following procedure describes the steps used to send data to a server.</span></span> <span data-ttu-id="5a679-104">Esse procedimento normalmente é usado para enviar dados para uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="5a679-104">This procedure is commonly used to post data to a Web page.</span></span>  
  
### <a name="to-send-data-to-a-host-server"></a><span data-ttu-id="5a679-105">Para enviar dados para um servidor de host</span><span class="sxs-lookup"><span data-stu-id="5a679-105">To send data to a host server</span></span>  
  
1.  <span data-ttu-id="5a679-106">Criar uma instância <xref:System.Net.WebRequest> chamando <xref:System.Net.WebRequest.Create%2A> com o URI do recurso que aceita dados, por exemplo, um script ou a página ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5a679-106">Create a <xref:System.Net.WebRequest> instance by calling <xref:System.Net.WebRequest.Create%2A> with the URI of the resource that accepts data, for example, a script or ASP.NET page.</span></span>  
  
    ```csharp  
    WebRequest request = WebRequest.Create("http://www.contoso.com/");  
    ```  
  
    ```vb  
    Dim request as WebRequest = WebRequest.Create("http://www.contoso.com/")  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a679-107">O .NET Framework fornece classes específicas de protocolo derivadas de **WebRequest** e **WebResponse** para URIs que começam com "http:", "https:", "ftp:" e "file:".</span><span class="sxs-lookup"><span data-stu-id="5a679-107">The .NET Framework provides protocol-specific classes derived from **WebRequest** and **WebResponse** for URIs that begin with "http:", "https:'', "ftp:", and "file:".</span></span> <span data-ttu-id="5a679-108">Para acessar recursos usando outros protocolos, você deve implementar classes específicas de protocolo derivadas de **WebRequest** e **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="5a679-108">To access resources using other protocols, you must implement protocol-specific classes that derive from **WebRequest** and **WebResponse**.</span></span> <span data-ttu-id="5a679-109">Para obter mais informações, consulte [Programando protocolos conectáveis](../../../docs/framework/network-programming/programming-pluggable-protocols.md).</span><span class="sxs-lookup"><span data-stu-id="5a679-109">For more information, see [Programming Pluggable Protocols](../../../docs/framework/network-programming/programming-pluggable-protocols.md) .</span></span>  
  
2.  <span data-ttu-id="5a679-110">Definir quaisquer valores de propriedade dos quais você precisa na **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="5a679-110">Set any property values that you need in the **WebRequest**.</span></span> <span data-ttu-id="5a679-111">Por exemplo, para habilitar a autenticação, defina a propriedade **Credentials** para uma instância da classe <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="5a679-111">For example, to enable authentication, set the **Credentials** property to an instance of the <xref:System.Net.NetworkCredential> class.</span></span>  
  
    ```csharp  
    request.Credentials = CredentialCache.DefaultCredentials;  
    ```  
  
    ```vb  
    request.Credentials = CredentialCache.DefaultCredentials  
    ```  
  
     <span data-ttu-id="5a679-112">Na maioria dos casos, a própria instância de **WebRequest** é suficiente para enviar dados.</span><span class="sxs-lookup"><span data-stu-id="5a679-112">In most cases, the **WebRequest** instance itself is sufficient to send data.</span></span> <span data-ttu-id="5a679-113">No entanto, se você precisar definir propriedades específicas de protocolo, você deverá converter a **WebRequest** para o tipo específico do protocolo.</span><span class="sxs-lookup"><span data-stu-id="5a679-113">However, if you need to set protocol-specific properties, you must cast the **WebRequest** to the protocol-specific type.</span></span> <span data-ttu-id="5a679-114">Por exemplo, acessar propriedades HTTP específicas de <xref:System.Net.HttpWebRequest>, converta a **WebRequest** para uma referência de **HttpWebRequest**.</span><span class="sxs-lookup"><span data-stu-id="5a679-114">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebRequest>, cast the **WebRequest** to an **HttpWebRequest** reference.</span></span> <span data-ttu-id="5a679-115">O exemplo de código a seguir mostra como definir a propriedade <xref:System.Net.HttpWebRequest.UserAgent%2A> específica de HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a679-115">The following code example shows how to set the HTTP-specific <xref:System.Net.HttpWebRequest.UserAgent%2A> property.</span></span>  
  
    ```csharp  
    ((HttpWebRequest)request).UserAgent = ".NET Framework Example Client";  
    ```  
  
    ```vb  
    Ctype(request,HttpWebRequest).UserAgent = ".NET Framework Example Client"  
    ```  
  
3.  <span data-ttu-id="5a679-116">Especifique um método de protocolo que permite que os dados sejam enviados com uma solicitação, tal como o método HTTP **POST**.</span><span class="sxs-lookup"><span data-stu-id="5a679-116">Specify a protocol method that permits data to be sent with a request, such as the HTTP **POST** method.</span></span>  
  
    ```csharp  
    request.Method = "POST";  
    ```  
  
    ```vb  
    request.Method = "POST"  
    ```  
  
4.  <span data-ttu-id="5a679-117">Defina a propriedade **ContentLength**.</span><span class="sxs-lookup"><span data-stu-id="5a679-117">Set the **ContentLength** property.</span></span>  
  
    ```csharp  
    request.ContentLength = byteArray.Length;  
    ```  
  
    ```vb  
    request.ContentLength = byteArray.Length  
    ```  
  
5.  <span data-ttu-id="5a679-118">Defina a propriedade **ContentType** para um valor apropriado.</span><span class="sxs-lookup"><span data-stu-id="5a679-118">Set the **ContentType** property to an appropriate value.</span></span>  
  
    ```csharp  
    request.ContentType = "application/x-www-form-urlencoded";  
    ```  
  
    ```vb  
    request.ContentType = "application/x-www-form-urlencoded"  
    ```  
  
6.  <span data-ttu-id="5a679-119">Obtenha o fluxo que mantém dados de solicitação chamando o método <xref:System.Net.WebRequest.GetRequestStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a679-119">Get the stream that holds request data by calling the <xref:System.Net.WebRequest.GetRequestStream%2A> method.</span></span>  
  
    ```csharp  
    Stream dataStream = request.GetRequestStream ();  
    ```  
  
    ```vb  
    Stream dataStream = request.GetRequestStream ()  
    ```  
  
7.  <span data-ttu-id="5a679-120">Grave os dados no objeto <xref:System.IO.Stream> retornado por este método.</span><span class="sxs-lookup"><span data-stu-id="5a679-120">Write the data to the <xref:System.IO.Stream> object returned by this method.</span></span>  
  
    ```csharp  
    dataStream.Write (byteArray, 0, byteArray.Length);  
    ```  
  
    ```vb  
    dataStream.Write (byteArray, 0, byteArray.Length)  
    ```  
  
8.  <span data-ttu-id="5a679-121">Feche o fluxo da solicitação chamando o método **Stream.Close**.</span><span class="sxs-lookup"><span data-stu-id="5a679-121">Close the request stream by calling the **Stream.Close** method.</span></span>  
  
    ```csharp  
    dataStream.Close ();  
    ```  
  
    ```vb  
    dataStream.Close ()  
    ```  
  
9. <span data-ttu-id="5a679-122">Envie a solicitação para o servidor chamando <xref:System.Net.WebRequest.GetResponse%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a679-122">Send the request to the server by calling <xref:System.Net.WebRequest.GetResponse%2A>.</span></span> <span data-ttu-id="5a679-123">Esse método retorna um objeto que contém a resposta do servidor.</span><span class="sxs-lookup"><span data-stu-id="5a679-123">This method returns an object containing the server's response.</span></span> <span data-ttu-id="5a679-124">O tipo do objeto <xref:System.Net.WebResponse> retornado é determinado pelo esquema do URI da solicitação.</span><span class="sxs-lookup"><span data-stu-id="5a679-124">The returned <xref:System.Net.WebResponse> object's type is determined by the scheme of the request's URI.</span></span>  
  
    ```csharp  
    WebResponse response = request.GetResponse();  
    ```  
  
    ```vb  
    Dim response As WebResponse = request.GetResponse()  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="5a679-125">Depois de terminar de usar um objeto <xref:System.Net.WebResponse>, você deve fechá-lo chamando o método <xref:System.Net.WebResponse.Close%2A>.</span><span class="sxs-lookup"><span data-stu-id="5a679-125">After you are finished with a <xref:System.Net.WebResponse> object, you must close it by calling the <xref:System.Net.WebResponse.Close%2A> method.</span></span> <span data-ttu-id="5a679-126">Alternativamente, se você obteve o fluxo de resposta do objeto de resposta, você pode fechar o fluxo chamando o método <xref:System.IO.Stream.Close%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5a679-126">Alternatively, if you have gotten the response stream from the response object, you can close the stream by calling the <xref:System.IO.Stream.Close%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="5a679-127">Se você não fechar a resposta ou o fluxo, o seu aplicativo poderá ficar sem conexões para o servidor e, nesse caso, ficará incapaz de processar solicitações adicionais.</span><span class="sxs-lookup"><span data-stu-id="5a679-127">If you do not close the response or the stream, your application can run out of connections to the server and become unable to process additional requests.</span></span>  
  
10. <span data-ttu-id="5a679-128">Você pode acessar as propriedades da **WebResponse** ou converter a **WebResponse** para uma instância específica de protocolo para ler as propriedades específicas de protocolo.</span><span class="sxs-lookup"><span data-stu-id="5a679-128">You can access the properties of the **WebResponse** or cast the **WebResponse** to a protocol-specific instance to read protocol-specific properties.</span></span> <span data-ttu-id="5a679-129">Por exemplo, para acessar as propriedades específicas de HTTP de <xref:System.Net.HttpWebResponse>, converta a **WebResponse** para uma referência de **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="5a679-129">For example, to access the HTTP-specific properties of <xref:System.Net.HttpWebResponse>, cast the **WebResponse** to an **HttpWebResponse** reference.</span></span>  
  
    ```csharp  
    Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
    ```  
  
    ```vb  
    Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
    ```  
  
11. <span data-ttu-id="5a679-130">Para obter o fluxo que contém os dados de resposta enviados pelo servidor, chame o método <xref:System.Net.WebResponse.GetResponseStream%2A> da **WebResponse**.</span><span class="sxs-lookup"><span data-stu-id="5a679-130">To get the stream containing response data sent by the server, call the <xref:System.Net.WebResponse.GetResponseStream%2A> method of the **WebResponse**.</span></span>  
  
    ```csharp  
    Stream data = response.GetResponseStream;  
    ```  
  
    ```vb  
    Dim data As Stream = response.GetResponseStream  
    ```  
  
12. <span data-ttu-id="5a679-131">Depois de ler os dados da resposta ou você deve fechar o fluxo de resposta usando o método **Stream.Close** ou fechar a resposta usando o método **WebResponse.Close**.</span><span class="sxs-lookup"><span data-stu-id="5a679-131">After reading the data from the response, you must either close the response stream using the **Stream.Close** method or close the response using the **WebResponse.Close** method.</span></span> <span data-ttu-id="5a679-132">Não é necessário chamar o método **Close** tanto no fluxo de resposta quanto na **WebResponse**, mas fazer isso não é prejudicial.</span><span class="sxs-lookup"><span data-stu-id="5a679-132">It is not necessary to call the **Close** method on both the response stream and the **WebResponse**, but doing so is not harmful.</span></span>  
  
    ```csharp  
    response.Close();  
    ```  
  
    ```vb  
    response.Close()  
    ```  
  
## <a name="example"></a><span data-ttu-id="5a679-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5a679-133">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestPostExample  
    {  
        public static void Main ()  
        {  
            // Create a request using a URL that can receive a post.   
            WebRequest request = WebRequest.Create ("http://www.contoso.com/PostAccepter.aspx ");  
            // Set the Method property of the request to POST.  
            request.Method = "POST";  
            // Create POST data and convert it to a byte array.  
            string postData = "This is a test that posts this string to a Web server.";  
            byte[] byteArray = Encoding.UTF8.GetBytes (postData);  
            // Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded";  
            // Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length;  
            // Get the request stream.  
            Stream dataStream = request.GetRequestStream ();  
            // Write the data to the request stream.  
            dataStream.Write (byteArray, 0, byteArray.Length);  
            // Close the Stream object.  
            dataStream.Close ();  
            // Get the response.  
            WebResponse response = request.GetResponse ();  
            // Display the status.  
            Console.WriteLine (((HttpWebResponse)response).StatusDescription);  
            // Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream ();  
            // Open the stream using a StreamReader for easy access.  
            StreamReader reader = new StreamReader (dataStream);  
            // Read the content.  
            string responseFromServer = reader.ReadToEnd ();  
            // Display the content.  
            Console.WriteLine (responseFromServer);  
            // Clean up the streams.  
            reader.Close ();  
            dataStream.Close ();  
            response.Close ();  
        }  
    }  
}  
```  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Net  
Imports System.Text  
Namespace Examples.System.Net  
    Public Class WebRequestPostExample  
  
        Public Shared Sub Main()  
            ' Create a request using a URL that can receive a post.   
            Dim request As WebRequest = WebRequest.Create("http://www.contoso.com/PostAccepter.aspx ")  
            ' Set the Method property of the request to POST.  
            request.Method = "POST"  
            ' Create POST data and convert it to a byte array.  
            Dim postData As String = "This is a test that posts this string to a Web server."  
            Dim byteArray As Byte() = Encoding.UTF8.GetBytes(postData)  
            ' Set the ContentType property of the WebRequest.  
            request.ContentType = "application/x-www-form-urlencoded"  
            ' Set the ContentLength property of the WebRequest.  
            request.ContentLength = byteArray.Length  
            ' Get the request stream.  
            Dim dataStream As Stream = request.GetRequestStream()  
            ' Write the data to the request stream.  
            dataStream.Write(byteArray, 0, byteArray.Length)  
            ' Close the Stream object.  
            dataStream.Close()  
            ' Get the response.  
            Dim response As WebResponse = request.GetResponse()  
            ' Display the status.  
            Console.WriteLine(CType(response, HttpWebResponse).StatusDescription)  
            ' Get the stream containing content returned by the server.  
            dataStream = response.GetResponseStream()  
            ' Open the stream using a StreamReader for easy access.  
            Dim reader As New StreamReader(dataStream)  
            ' Read the content.  
            Dim responseFromServer As String = reader.ReadToEnd()  
            ' Display the content.  
            Console.WriteLine(responseFromServer)  
            ' Clean up the streams.  
            reader.Close()  
            dataStream.Close()  
            response.Close()  
        End Sub  
    End Class  
End Namespace  
```  
  
## <a name="see-also"></a><span data-ttu-id="5a679-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a679-134">See Also</span></span>  
 <span data-ttu-id="5a679-135">[Criando solicitações da Internet](../../../docs/framework/network-programming/creating-internet-requests.md) </span><span class="sxs-lookup"><span data-stu-id="5a679-135">[Creating Internet Requests](../../../docs/framework/network-programming/creating-internet-requests.md) </span></span>  
 <span data-ttu-id="5a679-136">[Usando fluxos na rede](../../../docs/framework/network-programming/using-streams-on-the-network.md) </span><span class="sxs-lookup"><span data-stu-id="5a679-136">[Using Streams on the Network](../../../docs/framework/network-programming/using-streams-on-the-network.md) </span></span>  
 <span data-ttu-id="5a679-137">[Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span><span class="sxs-lookup"><span data-stu-id="5a679-137">[Accessing the Internet Through a Proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span></span>  
 <span data-ttu-id="5a679-138">[Solicitando dados](../../../docs/framework/network-programming/requesting-data.md) </span><span class="sxs-lookup"><span data-stu-id="5a679-138">[Requesting Data](../../../docs/framework/network-programming/requesting-data.md) </span></span>  
 [<span data-ttu-id="5a679-139">Como solicitar dados usando a classe WebRequest</span><span class="sxs-lookup"><span data-stu-id="5a679-139">How to: Request Data Using the WebRequest Class</span></span>](../../../docs/framework/network-programming/how-to-request-data-using-the-webrequest-class.md)
