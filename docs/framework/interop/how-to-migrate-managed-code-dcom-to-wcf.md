---
title: "Como: migrar código gerenciador do DCOM para o WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: 52961ffc-d1c7-4f83-832c-786444b951ba
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2d6077b9d5be8866aa22b884f61ad49f48ee9b0a
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-migrate-managed-code-dcom-to-wcf"></a><span data-ttu-id="3360b-102">Como: migrar código gerenciador do DCOM para o WCF</span><span class="sxs-lookup"><span data-stu-id="3360b-102">How to: Migrate Managed-Code DCOM to WCF</span></span>
<span data-ttu-id="3360b-103">O WCF (Windows Communication Foundation) é a opção recomendada e uma escolha segura no lugar do DCOM (Distributed Component Object Model) para chamadas de código gerenciado entre servidores e clientes em um ambiente distribuído.</span><span class="sxs-lookup"><span data-stu-id="3360b-103">Windows Communication Foundation (WCF) is the recommended and secure choice over Distributed Component Object Model (DCOM) for managed code calls between servers and clients in a distributed environment.</span></span> <span data-ttu-id="3360b-104">Este artigo mostra como migrar código de DCOM para o WCF para os cenários a seguir.</span><span class="sxs-lookup"><span data-stu-id="3360b-104">This article shows how you to migrate code from DCOM to WCF for the following scenarios.</span></span>  
  
-   <span data-ttu-id="3360b-105">O serviço remoto retorna um objeto por valor para o cliente</span><span class="sxs-lookup"><span data-stu-id="3360b-105">The remote service returns an object by-value to the client</span></span>  
  
-   <span data-ttu-id="3360b-106">O cliente envia um objeto por valor para o serviço remoto</span><span class="sxs-lookup"><span data-stu-id="3360b-106">The client sends an object by-value to the remote service</span></span>  
  
-   <span data-ttu-id="3360b-107">O serviço remoto retorna um objeto por referência para o cliente</span><span class="sxs-lookup"><span data-stu-id="3360b-107">The remote service returns an object by-reference to the client</span></span>  
  
 <span data-ttu-id="3360b-108">Por motivos de segurança, enviar um objeto por referência do cliente para o serviço não é permitido no WCF.</span><span class="sxs-lookup"><span data-stu-id="3360b-108">For security reasons, sending an object by-reference from the client to the service is not allowed in WCF.</span></span> <span data-ttu-id="3360b-109">Um cenário que requer uma conversa de ida e volta entre o cliente e o servidor pode ser obtido no WCF usando um serviço duplex.</span><span class="sxs-lookup"><span data-stu-id="3360b-109">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span>  <span data-ttu-id="3360b-110">Para obter mais informações sobre serviços duplex, consulte [Serviços duplex](../../../docs/framework/wcf/feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="3360b-110">For more information about duplex services, see [Duplex Services](../../../docs/framework/wcf/feature-details/duplex-services.md).</span></span>  
  
 <span data-ttu-id="3360b-111">Para obter mais detalhes sobre a criação de serviços do WCF e clientes para esses serviços, consulte [Programação WCF básica](../../../docs/framework/wcf/basic-wcf-programming.md), [Projetando e Implementando serviços](../../../docs/framework/wcf/designing-and-implementing-services.md) e [Compilando clientes](../../../docs/framework/wcf/building-clients.md).</span><span class="sxs-lookup"><span data-stu-id="3360b-111">For more details about creating WCF services and clients for those services, see [Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md), [Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md), and [Building Clients](../../../docs/framework/wcf/building-clients.md).</span></span>  
  
## <a name="dcom-example-code"></a><span data-ttu-id="3360b-112">Código de exemplo do DCOM</span><span class="sxs-lookup"><span data-stu-id="3360b-112">DCOM example code</span></span>  
 <span data-ttu-id="3360b-113">Nesses cenários, as interfaces DCOM ilustradas usando o WCF têm a seguinte estrutura:</span><span class="sxs-lookup"><span data-stu-id="3360b-113">For these scenarios, the DCOM interfaces that are illustrated using WCF have the following structure:</span></span>  
  
```  
[ComVisible(true)]  
[Guid("AA9C4CDB-55EA-4413-90D2-843F1A49E6E6")]  
public interface IRemoteService  
{  
   Customer GetObjectByValue();  
   IRemoteObject GetObjectByReference();  
   void SendObjectByValue(Customer customer);  
}  
  
[ComVisible(true)]  
[Guid("A12C98DE-B6A1-463D-8C24-81E4BBC4351B")]  
public interface IRemoteObject  
{  
}  
  
public class Customer  
{  
}  
```  
  
## <a name="the-service-returns-an-object-by-value"></a><span data-ttu-id="3360b-114">O serviço retorna um objeto por valor</span><span class="sxs-lookup"><span data-stu-id="3360b-114">The service returns an object by-value</span></span>  
 <span data-ttu-id="3360b-115">Para este cenário, você faz uma chamada para um serviço e método retorna um objeto, que é passado por valor do servidor para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-115">For this scenario, you make a call to a service and it method returns an object, which is passed by-value from the server to the client.</span></span> <span data-ttu-id="3360b-116">Esse cenário representa a chamada COM a seguir:</span><span class="sxs-lookup"><span data-stu-id="3360b-116">This scenario represents the following COM call:</span></span>  
  
```  
public interface IRemoteService  
{  
    Customer GetObjectByValue();  
}  
```  
  
 <span data-ttu-id="3360b-117">Nesse cenário, o cliente recebe uma cópia desserializada de um objeto do serviço remoto.</span><span class="sxs-lookup"><span data-stu-id="3360b-117">In this scenario, the client receives a deserialized copy of an object from the remote service.</span></span> <span data-ttu-id="3360b-118">O cliente pode interagir com essa cópia local sem fazer uma chamada de volta para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3360b-118">The client can interact with this local copy without calling back to the service.</span></span>  <span data-ttu-id="3360b-119">Em outras palavras, o cliente tem certeza de que o serviço não estará envolvido de nenhum modo quando os métodos na cópia local forem chamados.</span><span class="sxs-lookup"><span data-stu-id="3360b-119">In other words, the client is guaranteed the service will not be involved in any way when methods on the local copy are called.</span></span> <span data-ttu-id="3360b-120">O WCF sempre retorna objetos do serviço por valor, portanto, as etapas a seguir descrevem a criação de um serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="3360b-120">WCF always returns objects from the service by value, so the following steps describe creating a regular WCF service.</span></span>  
  
### <a name="step-1-define-the-wcf-service-interface"></a><span data-ttu-id="3360b-121">Etapa 1: definir a interface do serviço WCF</span><span class="sxs-lookup"><span data-stu-id="3360b-121">Step 1: Define the WCF service interface</span></span>  
 <span data-ttu-id="3360b-122">Defina uma interface pública para o serviço WCF e marque-a com o atributo [<xref:System.ServiceModel.ServiceContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="3360b-122">Define a public interface for the WCF service and mark it with the [<xref:System.ServiceModel.ServiceContractAttribute>] attribute.</span></span>  <span data-ttu-id="3360b-123">Marcar os métodos que você deseja expor para clientes com o atributo [<xref:System.ServiceModel.OperationContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="3360b-123">Mark the methods you want to expose to clients with the [<xref:System.ServiceModel.OperationContractAttribute>] attribute.</span></span> <span data-ttu-id="3360b-124">O exemplo a seguir mostra o uso desses atributos para identificar a interface do lado do servidor e métodos de interface que um cliente pode chamar.</span><span class="sxs-lookup"><span data-stu-id="3360b-124">The following example shows using these attributes to identify the server-side interface and interface methods a client can call.</span></span> <span data-ttu-id="3360b-125">O método usado para esse cenário é mostrado em negrito.</span><span class="sxs-lookup"><span data-stu-id="3360b-125">The method used for this scenario is shown in bold.</span></span>  
  
```  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Web;   
. . .  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]  
    void StoreCustomer(Customer customer);  
  
    [OperationContract]     Customer GetCustomer(string firstName, string lastName);   
  
}  
```  
  
### <a name="step-2-define-the-data-contract"></a><span data-ttu-id="3360b-126">Etapa 2: definir o contrato de dados</span><span class="sxs-lookup"><span data-stu-id="3360b-126">Step 2: Define the data contract</span></span>  
 <span data-ttu-id="3360b-127">Em seguida, você deve criar um contrato de dados para o serviço, que descreve como os dados serão trocados entre o serviço e seus clientes.</span><span class="sxs-lookup"><span data-stu-id="3360b-127">Next you should create a data contract for the service, which will describe how the data will be exchanged between the service and its clients.</span></span>  <span data-ttu-id="3360b-128">Classes descritas no contrato de dados devem ser marcadas com o atributo [<xref:System.Runtime.Serialization.DataContractAttribute>].</span><span class="sxs-lookup"><span data-stu-id="3360b-128">Classes described in the data contract should be marked with the [<xref:System.Runtime.Serialization.DataContractAttribute>] attribute.</span></span> <span data-ttu-id="3360b-129">As propriedades individuais ou campos que você quer que fiquem visíveis para o cliente e para o servidor devem ser marcados com o atributo [<xref:System.Runtime.Serialization.DataMemberAttribute>]. Se você quiser que tipos derivados de uma classe no contrato de dados sejam permitidos, você deverá identificá-los com o atributo [<xref:System.Runtime.Serialization.KnownTypeAttribute>].</span><span class="sxs-lookup"><span data-stu-id="3360b-129">The individual properties or fields you want visible to both client and server should be marked with the [<xref:System.Runtime.Serialization.DataMemberAttribute>] attribute.If you want types derived from a class in the data contract to be allowed, you must identify them with the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute.</span></span> <span data-ttu-id="3360b-130">WCF só será serializar ou desserializará tipos na interface do serviço e tipos identificados como conhecidos.</span><span class="sxs-lookup"><span data-stu-id="3360b-130">WCF will only serialize or deserialize types in the service interface and types identified as known types.</span></span> <span data-ttu-id="3360b-131">Se você tentar usar um tipo que não for um tipo conhecido, ocorrerá uma exceção.</span><span class="sxs-lookup"><span data-stu-id="3360b-131">If you attempt to use a type that is not a known type, an exception will occur.</span></span>  
  
 <span data-ttu-id="3360b-132">Para obter mais informações sobre contratos de dados, consulte [Contratos de dados](../../../docs/framework/wcf/samples/data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="3360b-132">For more information about data contracts, see [Data Contracts](../../../docs/framework/wcf/samples/data-contracts.md).</span></span>  
  
```  
[DataContract]  
[KnownType(typeof(PremiumCustomer))]  
public class Customer  
{  
    [DataMember]  
    public string Firstname;  
    [DataMember]  
    public string Lastname;  
    [DataMember]  
    public Address DefaultDeliveryAddress;  
    [DataMember]  
    public Address DefaultBillingAddress;  
}  
 [DataContract]  
public class PremiumCustomer : Customer  
{  
    [DataMember]  
    public int AccountID;  
}  
  
 [DataContract]  
public class Address  
{  
    [DataMember]  
    public string Street;  
    [DataMember]  
    public string Zipcode;  
    [DataMember]  
    public string City;  
    [DataMember]  
    public string State;  
    [DataMember]  
    public string Country;  
}  
```  
  
### <a name="step-3-implement-the-wcf-service"></a><span data-ttu-id="3360b-133">Etapa 3: implementar o serviço WCF</span><span class="sxs-lookup"><span data-stu-id="3360b-133">Step 3: Implement the WCF service</span></span>  
 <span data-ttu-id="3360b-134">Em seguida, você deve implementar a classe do serviço WCF que implementa a interface definida na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="3360b-134">Next, you should implement the WCF service class that implements the interface you defined in the previous step.</span></span>  
  
```  
public class CustomerService: ICustomerManager    
{  
    public void StoreCustomer(Customer customer)  
    {  
        // write to a database  
    }  
    public Customer GetCustomer(string firstName, string lastName)  
    {  
        // read from a database  
    }  
}  
```  
  
### <a name="step-4-configure-the-service-and-the-client"></a><span data-ttu-id="3360b-135">Etapa 4: configurar o serviço e o cliente</span><span class="sxs-lookup"><span data-stu-id="3360b-135">Step 4: Configure the service and the client</span></span>  
 <span data-ttu-id="3360b-136">Para executar um serviço WCF, é necessário declarar um ponto de extremidade que expõe essa interface de serviço em uma URL específica usando uma associação do WCF específica.</span><span class="sxs-lookup"><span data-stu-id="3360b-136">To run a WCF service, you need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="3360b-137">Uma associação especifica os detalhes de transporte, codificação e protocolo para a comunicação entre o servidor e os clientes.</span><span class="sxs-lookup"><span data-stu-id="3360b-137">A binding specifies the transport, encoding and protocol details for the clients and server to communicate.</span></span> <span data-ttu-id="3360b-138">Geralmente, você adiciona associações ao arquivo de configuração do projeto de serviço (web.config).</span><span class="sxs-lookup"><span data-stu-id="3360b-138">You typically add bindings to the service project’s configuration file (web.config).</span></span> <span data-ttu-id="3360b-139">O exemplo a seguir mostra uma entrada de associação para o serviço de exemplo:</span><span class="sxs-lookup"><span data-stu-id="3360b-139">The following shows a binding entry for the example service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Server.CustomerService">  
        <endpoint address="http://localhost:8083/CustomerManager"   
                  binding="basicHttpBinding"  
                  contract="Shared.ICustomerManager" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3360b-140">Em seguida, você precisa configurar o cliente de acordo com as informações de associação especificadas pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3360b-140">Next, you need to configure the client to match the binding information specified by the service.</span></span> <span data-ttu-id="3360b-141">Para fazer isso, adicione o seguinte ao arquivo de configuração (app.config) do aplicativo do cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-141">To do so, add the following to the client’s application configuration (app.config) file.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="customermanager"   
                address="http://localhost:8083/CustomerManager"   
                binding="basicHttpBinding"   
                contract="Shared.ICustomerManager"/>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="step-5-run-the-service"></a><span data-ttu-id="3360b-142">Etapa 5: executar o serviço</span><span class="sxs-lookup"><span data-stu-id="3360b-142">Step 5: Run the service</span></span>  
 <span data-ttu-id="3360b-143">Por fim, você pode fazer auto-hospedagem em um aplicativo de console, adicionando as linhas a seguir ao aplicativo de serviço e iniciando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3360b-143">Finally, you can self-host it in a console application by adding the following lines to the service app, and starting the app.</span></span> <span data-ttu-id="3360b-144">Para obter mais informações sobre outras maneiras de hospedar um aplicativo de serviço WCF, consulte [Serviços de hospedagem](../../../docs/framework/wcf/hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="3360b-144">For more information about other ways to host a WCF service application, [Hosting Services](../../../docs/framework/wcf/hosting-services.md).</span></span>  
  
```  
ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
customerServiceHost.Open();  
```  
  
### <a name="step-6-call-the-service-from-the-client"></a><span data-ttu-id="3360b-145">Etapa 6: chamar o serviço do cliente</span><span class="sxs-lookup"><span data-stu-id="3360b-145">Step 6: Call the service from the client</span></span>  
 <span data-ttu-id="3360b-146">Para chamar o serviço do cliente, você precisa criar uma fábrica de canais para o serviço e solicitar um canal, o que permitirá que você chame diretamente o método `GetCustomer`, diretamente do cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-146">To call the service from the client, you need to create a channel factory for the service, and request a channel, which will enable you to directly call the `GetCustomer` method directly from the client.</span></span> <span data-ttu-id="3360b-147">O canal implementa a interface do serviço e manipula a lógica subjacente de solicitação/resposta para você.</span><span class="sxs-lookup"><span data-stu-id="3360b-147">The channel implements the service’s interface and handles the underlying request/reply logic for you.</span></span>  <span data-ttu-id="3360b-148">O valor retornado dessa chamada de método que é a cópia desserializada da resposta do serviço.</span><span class="sxs-lookup"><span data-stu-id="3360b-148">The return value from that method call is the deserialized copy of the service response.</span></span>  
  
```  
ChannelFactory<ICustomerManager> factory =   
     new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager service = factory.CreateChannel();  
Customer customer = service.GetCustomer("Mary", "Smith");  
```  
  
## <a name="the-client-sends-a-by-value-object-to-the-server"></a><span data-ttu-id="3360b-149">O cliente envia um objeto por valor para o servidor</span><span class="sxs-lookup"><span data-stu-id="3360b-149">The client sends a by-value object to the server</span></span>  
 <span data-ttu-id="3360b-150">Nesse cenário, o cliente envia um objeto para o servidor, por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-150">In this scenario, the client sends an object to the server, by-value.</span></span> <span data-ttu-id="3360b-151">Isso significa que o servidor receberá uma cópia desserializada do objeto.</span><span class="sxs-lookup"><span data-stu-id="3360b-151">This means that the server will receive a deserialized copy of the object.</span></span>  <span data-ttu-id="3360b-152">O servidor pode chamar métodos de cópia e obter a garantia de que não há nenhum retorno de chamada no código do cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-152">The server can call methods on that copy and be guaranteed there is no callback into client code.</span></span> <span data-ttu-id="3360b-153">Conforme mencionado anteriormente, as trocas de dados de WCF normais são por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-153">As mentioned previously, normal WCF exchanges of data are by-value.</span></span>  <span data-ttu-id="3360b-154">Isso garante que chamar métodos em um desses objetos resultará apenas em execução local – não invocará código no cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-154">This guarantees that calling methods on one of these objects executes locally only – it will not invoke code on the client.</span></span>  
  
 <span data-ttu-id="3360b-155">Esse cenário representa a chamada de método COM a seguir:</span><span class="sxs-lookup"><span data-stu-id="3360b-155">This scenario represents the following COM method call:</span></span>  
  
```  
public interface IRemoteService  
{  
    void SendObjectByValue(Customer customer);  
}  
```  
  
 <span data-ttu-id="3360b-156">Esse cenário usa o mesmo contrato de dados e interface de serviço, conforme mostrado no primeiro exemplo.</span><span class="sxs-lookup"><span data-stu-id="3360b-156">This scenario uses the same service interface and data contract as shown in the first example.</span></span> <span data-ttu-id="3360b-157">Além disso, o cliente e o serviço serão configurados da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="3360b-157">In addition, the client and service will be configured in the same way.</span></span> <span data-ttu-id="3360b-158">Neste exemplo, um canal é criado para enviar o objeto e executar da mesma maneira.</span><span class="sxs-lookup"><span data-stu-id="3360b-158">In this example, a channel is created to send the object and run the same way.</span></span> <span data-ttu-id="3360b-159">No entanto, neste exemplo, você criará um cliente que chamará o serviço, passando um objeto por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-159">However, for this example, you will create a client that calls the service, passing an object by-value.</span></span> <span data-ttu-id="3360b-160">O método de serviço que o cliente chamará no contrato de serviço é mostrado em negrito:</span><span class="sxs-lookup"><span data-stu-id="3360b-160">The service method the client will call in the service contract is shown in bold:</span></span>  
  
```  
[ServiceContract]  
public interface ICustomerManager  
{  
    [OperationContract]     void StoreCustomer(Customer customer);  
  
    [OperationContract]  
    Customer GetCustomer(string firstName, string lastName);  
}  
```  
  
### <a name="add-code-to-the-client-that-sends-a-by-value-object"></a><span data-ttu-id="3360b-161">Adicionar código para o cliente que envia um objeto por valor</span><span class="sxs-lookup"><span data-stu-id="3360b-161">Add code to the client that sends a by-value object</span></span>  
 <span data-ttu-id="3360b-162">O código a seguir mostra como o cliente cria um novo objeto de cliente por valor, cria um canal para se comunicar com o serviço `ICustomerManager` e envia o objeto de cliente para ele.</span><span class="sxs-lookup"><span data-stu-id="3360b-162">The following code shows how the client creates a new by-value customer object, creates a channel to communicate with the `ICustomerManager` service, and sends the customer object to it.</span></span>  
  
 <span data-ttu-id="3360b-163">O objeto de cliente será serializado e enviado para o serviço, em que ele será desserializado pelo serviço gerando uma nova cópia desse objeto.</span><span class="sxs-lookup"><span data-stu-id="3360b-163">The customer object will be serialized, and sent to the service, where it is deserialized by the service into a new copy of that object.</span></span>  <span data-ttu-id="3360b-164">Qualquer método chamado pelo serviço nesse objeto será executado apenas localmente no servidor. É importante observar que esse código ilustra o envio de um tipo derivado (`PremiumCustomer`).</span><span class="sxs-lookup"><span data-stu-id="3360b-164">Any methods the service calls on this object will execute only locally on the server.It’s important to note that this code illustrates sending a derived type (`PremiumCustomer`).</span></span>  <span data-ttu-id="3360b-165">O contrato de serviço espera um objeto `Customer`, mas o contrato de dados de serviço usa o atributo [<xref:System.Runtime.Serialization.KnownTypeAttribute>] para indicar que `PremiumCustomer` também é permitido.</span><span class="sxs-lookup"><span data-stu-id="3360b-165">The service contract expects a `Customer` object, but the service data contract uses the [<xref:System.Runtime.Serialization.KnownTypeAttribute>] attribute to indicate that `PremiumCustomer` is also allowed.</span></span>  <span data-ttu-id="3360b-166">As tentativas do WCF de serializar ou desserializar qualquer outro tipo via interface de serviço falharão.</span><span class="sxs-lookup"><span data-stu-id="3360b-166">WCF will fail attempts to serialize or deserialize any other type via this service interface.</span></span>  
  
```  
PremiumCustomer customer = new PremiumCustomer();  
customer.Firstname = "John";  
customer.Lastname = "Doe";  
customer.DefaultBillingAddress = new Address();  
customer.DefaultBillingAddress.Street = "One Microsoft Way";  
customer.DefaultDeliveryAddress = customer.DefaultBillingAddress;  
customer.AccountID = 42;  
  
ChannelFactory<ICustomerManager> factory =  
   new ChannelFactory<ICustomerManager>("customermanager");  
ICustomerManager customerManager = factory.CreateChannel();  
customerManager.StoreCustomer(customer);  
```  
  
## <a name="the-service-returns-an-object-by-reference"></a><span data-ttu-id="3360b-167">O serviço retorna um objeto por referência</span><span class="sxs-lookup"><span data-stu-id="3360b-167">The service returns an object by reference</span></span>  
 <span data-ttu-id="3360b-168">Para este cenário, o aplicativo cliente faz uma chamada para o serviço remoto e o método retorna um objeto, que é passado por referência do serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="3360b-168">For this scenario, the client app makes a call to the remote service and the method returns an object, which is passed by reference from the service to the client.</span></span>  
  
 <span data-ttu-id="3360b-169">Conforme mencionado anteriormente, os serviços WCF sempre retornam o objeto por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-169">As mentioned previously, WCF services always return object by value.</span></span>  <span data-ttu-id="3360b-170">No entanto, você pode obter um resultado semelhante usando a classe <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="3360b-170">However, you can achieve a similar result by using the <xref:System.ServiceModel.EndpointAddress10> class.</span></span>  <span data-ttu-id="3360b-171">O <xref:System.ServiceModel.EndpointAddress10> é um objeto serializável por valor que pode ser usado pelo cliente para obter um objeto por referência de sessão no servidor.</span><span class="sxs-lookup"><span data-stu-id="3360b-171">The <xref:System.ServiceModel.EndpointAddress10> is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span>  
  
 <span data-ttu-id="3360b-172">O comportamento do objeto por referência no WCF mostrado nesse cenário é diferente do observado com DCOM.</span><span class="sxs-lookup"><span data-stu-id="3360b-172">The behavior of the by-reference object in WCF shown in this scenario is different than DCOM.</span></span>  <span data-ttu-id="3360b-173">No DCOM, o servidor pode retornar um objeto por referência para o cliente diretamente e o cliente pode chamar os métodos desse objeto, que são executados no servidor.</span><span class="sxs-lookup"><span data-stu-id="3360b-173">In DCOM, the server can return a by-reference object to the client directly, and the client can call that object’s methods, which execute on the server.</span></span>  <span data-ttu-id="3360b-174">No entanto, no WCF, o objeto retornado é sempre por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-174">In WCF, however, the object returned is always by-value.</span></span>  <span data-ttu-id="3360b-175">O cliente deve tomar esse objeto por valor representado por <xref:System.ServiceModel.EndpointAddress10> e usá-lo para criar seu próprio objeto de sessão por referência.</span><span class="sxs-lookup"><span data-stu-id="3360b-175">The client must take that by-value object, represented by <xref:System.ServiceModel.EndpointAddress10> and use it to create its own sessionful by-reference object.</span></span>  <span data-ttu-id="3360b-176">As chamadas de método do cliente no objeto de sessão são executadas no servidor. Em outras palavras, esse objeto por referência no WCF é um serviço WCF normal que está configurado para ser de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-176">The client method calls on the sessionful object execute on the server.In other words, this by-reference object in WCF is a normal WCF service that is configured to be sessionful.</span></span>  
  
 <span data-ttu-id="3360b-177">No WCF, uma sessão é uma maneira de correlacionar várias mensagens enviadas entre dois pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="3360b-177">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span>  <span data-ttu-id="3360b-178">Isso significa que, depois que um cliente obtiver uma conexão para esse serviço, uma sessão será estabelecida entre o cliente e o servidor.</span><span class="sxs-lookup"><span data-stu-id="3360b-178">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span>  <span data-ttu-id="3360b-179">O cliente usará uma única instância exclusiva do objeto do lado do servidor para todas as interações dele nessa única sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-179">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span> <span data-ttu-id="3360b-180">Contratos WCF de sessão são semelhantes aos padrões de solicitação/resposta de rede voltados para conexão.</span><span class="sxs-lookup"><span data-stu-id="3360b-180">Sessionful WCF contracts are similar to connection-oriented network request/response patterns.</span></span>  
  
 <span data-ttu-id="3360b-181">Esse cenário é representado pelo método DCOM a seguir.</span><span class="sxs-lookup"><span data-stu-id="3360b-181">This scenario is represented by the following DCOM method.</span></span>  
  
```  
public interface IRemoteService  
{  
    IRemoteObject GetObjectByReference();  
}  
```  
  
### <a name="step-1-define-the-sessionful-wcf-service-interface-and-implementation"></a><span data-ttu-id="3360b-182">Etapa 1: definir a interface do serviço WCF de sessão e implementação</span><span class="sxs-lookup"><span data-stu-id="3360b-182">Step 1: Define the Sessionful WCF service interface and implementation</span></span>  
 <span data-ttu-id="3360b-183">Primeiro, defina uma interface de serviço WCF que contém o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-183">First, define a WCF service interface that contains the sessionful object.</span></span>  
  
 <span data-ttu-id="3360b-184">Nesse código, o objeto de sessão é marcado com o atributo `ServiceContract`, que o identifica como uma interface de serviço WCF normal.</span><span class="sxs-lookup"><span data-stu-id="3360b-184">In this code, the sessionful object is marked with the `ServiceContract` attribute, which identifies it as a regular WCF service interface.</span></span>  <span data-ttu-id="3360b-185">Além disso, a propriedade <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> é definida para indicar que ele será um serviço de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-185">In addition, the <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> property is set to indicate it will be a sessionful service.</span></span>  
  
```  
[ServiceContract(SessionMode = SessionMode.Allowed)]  
public interface ISessionBoundObject  
{  
    [OperationContract]  
    string GetCurrentValue();  
  
    [OperationContract]  
    void SetCurrentValue(string value);  
}  
```  
  
 <span data-ttu-id="3360b-186">O código a seguir mostra a implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="3360b-186">The following code shows the service implementation.</span></span>  
  
 <span data-ttu-id="3360b-187">O serviço é marcado com o atributo [ServiceBehavior] e a propriedade InstanceContextMode dele é definida como InstanceContextMode.PerSessions para indicar que uma instância exclusiva desse tipo deve ser criada para cada sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-187">The service is marked with the [ServiceBehavior] attribute, and its InstanceContextMode property set to InstanceContextMode.PerSessions to indicate that a unique instance of this type should be created for each session.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
    public class MySessionBoundObject : ISessionBoundObject  
    {  
        private string _value;  
  
        public string GetCurrentValue()  
        {  
            return _value;  
        }  
  
        public void SetCurrentValue(string val)  
        {  
            _value = val;  
        }  
  
    }  
```  
  
### <a name="step-2-define-the-wcf-factory-service-for-the-sessionful-object"></a><span data-ttu-id="3360b-188">Etapa 2: definir o serviço de fábrica do WCF para o objeto de sessão</span><span class="sxs-lookup"><span data-stu-id="3360b-188">Step 2: Define the WCF factory service for the sessionful object</span></span>  
 <span data-ttu-id="3360b-189">O serviço que cria o objeto de sessão deve ser definido e implementado.</span><span class="sxs-lookup"><span data-stu-id="3360b-189">The service that creates the sessionful object must be defined and implemented.</span></span> <span data-ttu-id="3360b-190">O código a seguir mostra como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="3360b-190">The following code shows how to do this.</span></span> <span data-ttu-id="3360b-191">Esse código cria outro serviço WCF que retorna um objeto <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="3360b-191">This code creates another WCF service that returns an <xref:System.ServiceModel.EndpointAddress10> object.</span></span>  <span data-ttu-id="3360b-192">Essa é uma forma serializável de um ponto de extremidade que pode ser usada para criar o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-192">This is a serializable form of an endpoint the can use to create the session-full object.</span></span>  
  
```  
[ServiceContract]  
    public interface ISessionBoundFactory  
    {  
        [OperationContract]  
        EndpointAddress10 GetInstanceAddress();  
    }  
```  
  
 <span data-ttu-id="3360b-193">A seguir está a implementação desse serviço.</span><span class="sxs-lookup"><span data-stu-id="3360b-193">Following is the implementation of this service.</span></span> <span data-ttu-id="3360b-194">Essa implementação mantém uma fábrica de canais única para criar objetos de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-194">This implementation maintains a singleton channel factory to create sessionful objects.</span></span>  <span data-ttu-id="3360b-195">Quando `GetInstanceAddress` é chamado, ele cria um canal e cria um objeto <xref:System.ServiceModel.EndpointAddress10> que aponta para o endereço remoto associado a esse canal.</span><span class="sxs-lookup"><span data-stu-id="3360b-195">When `GetInstanceAddress` is called, it creates a channel and creates an <xref:System.ServiceModel.EndpointAddress10> object that points to the remote address associated with this channel.</span></span>   <span data-ttu-id="3360b-196"><xref:System.ServiceModel.EndpointAddress10> é um tipo de dados que pode ser retornado ao cliente por valor.</span><span class="sxs-lookup"><span data-stu-id="3360b-196"><xref:System.ServiceModel.EndpointAddress10> is a data type that can be returned to the client by-value.</span></span>  
  
```  
public class SessionBoundFactory : ISessionBoundFactory  
    {  
        public static ChannelFactory<ISessionBoundObject> _factory =   
            new ChannelFactory<ISessionBoundObject>("sessionbound");  
  
        public SessionBoundFactory()  
        {  
        }  
  
        public EndpointAddress10 GetInstanceAddress()  
        {  
            IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
            return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
        }  
    }  
```  
  
### <a name="step-3-configure-and-start-the-wcf-services"></a><span data-ttu-id="3360b-197">Etapa 3: configurar e iniciar os serviços WCF</span><span class="sxs-lookup"><span data-stu-id="3360b-197">Step 3: Configure and start the WCF services</span></span>  
 <span data-ttu-id="3360b-198">Para hospedar esses serviços, você precisará fazer as adições a seguir ao arquivo de configuração do servidor (web.config).</span><span class="sxs-lookup"><span data-stu-id="3360b-198">To host these services, you will need to make the following additions to the server’s configuration file (web.config).</span></span>  
  
1.  <span data-ttu-id="3360b-199">Adicione uma seção `<client>` que descreve o ponto de extremidade para o objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-199">Add a `<client>` section that describes the endpoint for the sessionful object.</span></span>  <span data-ttu-id="3360b-200">Nesse cenário, o servidor também atua como um cliente e deve ser configurado para permitir isso.</span><span class="sxs-lookup"><span data-stu-id="3360b-200">In this scenario, the server also acts as a client and must be configured to enable this.</span></span>  
  
2.  <span data-ttu-id="3360b-201">Na seção `<services>`, declare pontos de extremidade de serviço para a o objeto de fábrica e de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-201">In the `<services>` section, declare service endpoints for the factory and sessionful object.</span></span>  <span data-ttu-id="3360b-202">Isso permite que o cliente se comunique com os pontos de extremidade de serviço, adquira o <xref:System.ServiceModel.EndpointAddress10> e crie o canal de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-202">This enables the client to communicate with the service endpoints, acquire the <xref:System.ServiceModel.EndpointAddress10> and create the sessionful channel.</span></span>  
  
 <span data-ttu-id="3360b-203">A seguir está um exemplo de arquivo de configuração com essas configurações:</span><span class="sxs-lookup"><span data-stu-id="3360b-203">Following is an example configuration file with these settings:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"  
                address="net.tcp://localhost:8081/SessionBoundObject"  
                binding="netTcpBinding"  
                contract="Shared.ISessionBoundObject"/>  
    </client>  
  
    <services>  
      <service name="Server.MySessionBoundObject">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundObject" />  
      </service>  
      <service name="Server.SessionBoundFactory">  
        <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                  binding="netTcpBinding"   
                  contract="Shared.ISessionBoundFactory" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3360b-204">Adicione as linhas a seguir a um aplicativo de console, para hospedar automaticamente o serviço e iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="3360b-204">Add the following lines to a console application, to self-host the service, and start the app.</span></span>  
  
```  
ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
factoryHost.Open();  
  
ServiceHost sessionBoundServiceHost = new ServiceHost(  
typeof(MySessionBoundObject));  
sessionBoundServiceHost.Open();  
```  
  
### <a name="step-4-configure-the-client-and-call-the-service"></a><span data-ttu-id="3360b-205">Etapa 4: configurar o cliente e chamar o serviço</span><span class="sxs-lookup"><span data-stu-id="3360b-205">Step 4: Configure the client and call the service</span></span>  
 <span data-ttu-id="3360b-206">Configure o cliente para se comunicar com os serviços WCF, criando as seguintes entradas no arquivo de configuração de aplicativo do projeto (app.config).</span><span class="sxs-lookup"><span data-stu-id="3360b-206">Configure the client to communicate with the WCF services by making the following entries in the project’s application configuration file (app.config).</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint name="sessionbound"   
                address="net.tcp://localhost:8081/SessionBoundObject"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundObject"/>  
      <endpoint name="factory"   
                address="net.tcp://localhost:8081/SessionBoundFactory"   
                binding="netTcpBinding"   
                contract="Shared.ISessionBoundFactory"/>  
    </client>    
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3360b-207">Para chamar o serviço, adicione o código ao cliente para fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="3360b-207">To call the service, add the code to the client to do the following:</span></span>  
  
1.  <span data-ttu-id="3360b-208">Crie um canal para o serviço `ISessionBoundFactory`.</span><span class="sxs-lookup"><span data-stu-id="3360b-208">Create a channel to the `ISessionBoundFactory` service.</span></span>  
  
2.  <span data-ttu-id="3360b-209">Use o canal para invocar o serviço `ISessionBoundFactory` e obter um objeto <xref:System.ServiceModel.EndpointAddress10>.</span><span class="sxs-lookup"><span data-stu-id="3360b-209">Use the channel to invoke the `ISessionBoundFactory` service an obtain an <xref:System.ServiceModel.EndpointAddress10> bbject.</span></span>  
  
3.  <span data-ttu-id="3360b-210">Use o <xref:System.ServiceModel.EndpointAddress10> para criar um canal para obter um objeto de sessão.</span><span class="sxs-lookup"><span data-stu-id="3360b-210">Use the <xref:System.ServiceModel.EndpointAddress10> to create a channel to obtain a sessionful object.</span></span>  
  
4.  <span data-ttu-id="3360b-211">Chame os métodos `SetCurrentValue` e `GetCurrentValue` para demonstrar que ela permanece a mesma instância do objeto que é usada em várias chamadas.</span><span class="sxs-lookup"><span data-stu-id="3360b-211">Call the `SetCurrentValue` and `GetCurrentValue` methods to demonstrate it remains the same object instance is used across multiple calls.</span></span>  
  
```  
ChannelFactory<ISessionBoundFactory> factory =  
        new ChannelFactory<ISessionBoundFactory>("factory");  
  
ISessionBoundFactory sessionBoundFactory = factory.CreateChannel();  
  
EndpointAddress10 address = sessionBoundFactory.GetInstanceAddress();  
  
ChannelFactory<ISessionBoundObject> sessionBoundObjectFactory =  
    new ChannelFactory<ISessionBoundObject>(  
        new NetTcpBinding(),  
        address.ToEndpointAddress());  
  
ISessionBoundObject sessionBoundObject =  
        sessionBoundObjectFactory.CreateChannel();  
  
sessionBoundObject.SetCurrentValue("Hello");  
if (sessionBoundObject.GetCurrentValue() == "Hello")  
{  
    Console.WriteLine("Session-full instance management works as expected");  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3360b-212">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3360b-212">See Also</span></span>  
 <span data-ttu-id="3360b-213">[Programação de WCF básica](../../../docs/framework/wcf/basic-wcf-programming.md) </span><span class="sxs-lookup"><span data-stu-id="3360b-213">[Basic WCF Programming](../../../docs/framework/wcf/basic-wcf-programming.md) </span></span>  
 <span data-ttu-id="3360b-214">[Serviços de design e implantação](../../../docs/framework/wcf/designing-and-implementing-services.md) </span><span class="sxs-lookup"><span data-stu-id="3360b-214">[Designing and Implementing Services](../../../docs/framework/wcf/designing-and-implementing-services.md) </span></span>  
 <span data-ttu-id="3360b-215">[Compilando clientes](../../../docs/framework/wcf/building-clients.md) </span><span class="sxs-lookup"><span data-stu-id="3360b-215">[Building Clients](../../../docs/framework/wcf/building-clients.md) </span></span>  
 [<span data-ttu-id="3360b-216">Serviços duplex</span><span class="sxs-lookup"><span data-stu-id="3360b-216">Duplex Services</span></span>](../../../docs/framework/wcf/feature-details/duplex-services.md)
