---
title: "Como substituir a serialização XML de SOAP codificada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
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
- overriding XML serialization
- SOAP, overriding encoded XML serialization
ms.assetid: d0791df8-04e3-46b4-a6be-fe0ed09267e8
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 0dea6233f2a13bd3b6c7e33ebf9ee1c96dae7577
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-override-encoded-soap-xml-serialization"></a><span data-ttu-id="18712-102">Como substituir a serialização XML de SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="18712-102">How to: Override Encoded SOAP XML Serialization</span></span>
[<span data-ttu-id="18712-103">Exemplo de código</span><span class="sxs-lookup"><span data-stu-id="18712-103">Code Example</span></span>](#tskhowtooverrideencodedsoapxmlserializationanchor1)  
  
 <span data-ttu-id="18712-104">O processo para substituir a serialização XML de objetos, como mensagens SOAP é semelhante ao processo para substituir a serialização XML padrão.</span><span class="sxs-lookup"><span data-stu-id="18712-104">The process for overriding XML serialization of objects as SOAP messages is similar to the process for overriding standard XML serialization.</span></span> <span data-ttu-id="18712-105">Para obter informações sobre como substituir a serialização de XML padrão, consulte [Como especificar um nome de elemento alternativo para um fluxo XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="18712-105">For information about overriding standard XML serialization, see [How to: Specify an Alternate Element Name for an XML Stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>  
  
### <a name="to-override-serialization-of-objects-as-soap-messages"></a><span data-ttu-id="18712-106">Para substituir a serialização XML de objetos como mensagens SOAP</span><span class="sxs-lookup"><span data-stu-id="18712-106">To override serialization of objects as SOAP messages</span></span>  
  
1.  <span data-ttu-id="18712-107">Crie uma instância da classe <xref:System.Xml.Serialization.SoapAttributeOverrides>.</span><span class="sxs-lookup"><span data-stu-id="18712-107">Create an instance of the <xref:System.Xml.Serialization.SoapAttributeOverrides> class.</span></span>  
  
2.  <span data-ttu-id="18712-108">Crie um `SoapAttributes` para cada membro de classe que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="18712-108">Create a `SoapAttributes` for each class member that is being serialized.</span></span>  
  
3.  <span data-ttu-id="18712-109">Crie uma instância de um ou mais atributos que afetam a serialização XML, conforme for apropriado, para o membro que está sendo serializado.</span><span class="sxs-lookup"><span data-stu-id="18712-109">Create an instance of one or more of the attributes that affect XML serialization, as appropriate, to the member being serialized.</span></span> <span data-ttu-id="18712-110">Para obter mais informações, consulte "Atributos que controlam a serialização SOAP codificada".</span><span class="sxs-lookup"><span data-stu-id="18712-110">For more information, see "Attributes That Control Encoded SOAP Serialization".</span></span>  
  
4.  <span data-ttu-id="18712-111">Consulte a propriedade apropriada de `SoapAttributes` para o atributo criado na etapa 3.</span><span class="sxs-lookup"><span data-stu-id="18712-111">Set the appropriate property of `SoapAttributes` to the attribute created in step 3.</span></span>  
  
5.  <span data-ttu-id="18712-112">Adicione `SoapAttributes` a `SoapAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="18712-112">Add `SoapAttributes` to `SoapAttributeOverrides`.</span></span>  
  
6.  <span data-ttu-id="18712-113">Crie um `XmlTypeMapping` usando o `SoapAttributeOverrides`.</span><span class="sxs-lookup"><span data-stu-id="18712-113">Create an `XmlTypeMapping` using the `SoapAttributeOverrides`.</span></span> <span data-ttu-id="18712-114">Use o método `SoapReflectionImporter.ImportTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="18712-114">Use the `SoapReflectionImporter.ImportTypeMapping` method.</span></span>  
  
7.  <span data-ttu-id="18712-115">Crie um `XmlSerializer` usando `XmlTypeMapping`.</span><span class="sxs-lookup"><span data-stu-id="18712-115">Create an `XmlSerializer` using `XmlTypeMapping`.</span></span>  
  
8.  <span data-ttu-id="18712-116">Serialize ou desserialize o objeto.</span><span class="sxs-lookup"><span data-stu-id="18712-116">Serialize or deserialize the object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18712-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18712-117">Example</span></span>  
 <span data-ttu-id="18712-118">O exemplo de código a seguir serializa um arquivo de duas maneiras: primeiro, sem substituir o comportamento da classe `XmlSerializer` e, segundo, substituindo o comportamento.</span><span class="sxs-lookup"><span data-stu-id="18712-118">The following code example serializes a file in two ways: first, without overriding the `XmlSerializer` class's behavior, and second, by overriding the behavior.</span></span> <span data-ttu-id="18712-119">O exemple contém uma classe denominada `Group` com vários membros.</span><span class="sxs-lookup"><span data-stu-id="18712-119">The example contains a class named `Group` with several members.</span></span> <span data-ttu-id="18712-120">Vários atributos, como o `SoapElementAttribute`, foram aplicados aos membros da classe.</span><span class="sxs-lookup"><span data-stu-id="18712-120">Various attributes, such as the `SoapElementAttribute`, have been applied to class members.</span></span> <span data-ttu-id="18712-121">Quando a classe é serializada com o método `SerializeOriginal`, os atributos controlam o conteúdo da mensagem SOAP.</span><span class="sxs-lookup"><span data-stu-id="18712-121">When the class is serialized with the `SerializeOriginal` method, the attributes control the SOAP message content.</span></span> <span data-ttu-id="18712-122">Quando o método `SerializeOverride` é chamado, o comportamento do `XmlSerializer` é substituído criando vários atributos e definindo as propriedades de um `SoapAttributes` para esses atributos (conforme for apropriado).</span><span class="sxs-lookup"><span data-stu-id="18712-122">When the `SerializeOverride` method is called, the behavior of the `XmlSerializer` is overridden by creating various attributes and setting the properties of a `SoapAttributes` to those attributes (as appropriate).</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Schema;  
  
public class Group  
{  
    [SoapAttribute (Namespace = "http://www.cpandl.com")]  
    public string GroupName;  
  
    [SoapAttribute(DataType = "base64Binary")]  
    public Byte [] GroupNumber;  
  
    [SoapAttribute(DataType = "date", AttributeName = "CreationDate")]  
    public DateTime Today;  
    [SoapElement(DataType = "nonNegativeInteger", ElementName = "PosInt")]  
    public string PostitiveInt;  
    // This is ignored when serialized unless it is overridden.  
    [SoapIgnore]   
    public bool IgnoreThis;  
  
    public GroupType Grouptype;  
  
    [SoapInclude(typeof(Car))]  
    public Vehicle myCar(string licNumber)  
    {  
        Vehicle v;  
        if(licNumber == "")  
            {  
                v = new Car();  
            v.licenseNumber = "!!!!!!";  
        }  
        else  
        {  
            v = new Car();  
            v.licenseNumber = licNumber;  
        }  
        return v;  
    }  
}  
  
public abstract class Vehicle  
{  
    public string licenseNumber;  
    public DateTime makeDate;  
}  
  
public class Car: Vehicle  
{  
}  
  
public enum GroupType  
{  
    // These enums can be overridden.  
    small,  
    large  
}  
  
public class Run  
{  
    public static void Main()  
    {  
        Run test = new Run();  
        test.SerializeOriginal("SoapOriginal.xml");  
        test.SerializeOverride("SoapOverrides.xml");  
        test.DeserializeOriginal("SoapOriginal.xml");  
        test.DeserializeOverride("SoapOverrides.xml");  
  
    }  
    public void SerializeOriginal(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlTypeMapping myMapping =   
        (new SoapReflectionImporter().ImportTypeMapping(  
        typeof(Group)));  
        XmlSerializer mySerializer =    
        new XmlSerializer(myMapping);  
  
        // Writing the file requires a TextWriter.  
        TextWriter writer = new StreamWriter(filename);  
  
        // Creates an instance of the class that will be serialized.  
        Group myGroup = new Group();  
  
        // Sets the object properties.  
        myGroup.GroupName = ".NET";  
  
        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),  
        Convert.ToByte(50)};  
        myGroup.GroupNumber = hexByte;  
  
        DateTime myDate = new DateTime(2002,5,2);  
        myGroup.Today = myDate;  
  
        myGroup.PostitiveInt= "10000";  
        myGroup.IgnoreThis=true;  
        myGroup.Grouptype= GroupType.small;  
        Car thisCar =(Car)  myGroup.myCar("1234566");  
  
        // Prints the license number just to prove the car was created.  
        Console.WriteLine("License#: " + thisCar.licenseNumber + "\n");  
  
        // Serializes the class and closes the TextWriter.  
        mySerializer.Serialize(writer, myGroup);  
        writer.Close();  
    }  
  
    public void SerializeOverride(string filename)  
    {  
        // Creates an instance of the XmlSerializer class  
        // that overrides the serialization.  
        XmlSerializer overRideSerializer = CreateOverrideSerializer();  
  
        // Writing the file requires a TextWriter.  
        TextWriter writer = new StreamWriter(filename);  
  
        // Creates an instance of the class that will be serialized.  
        Group myGroup = new Group();  
  
        // Sets the object properties.  
        myGroup.GroupName = ".NET";  
  
        Byte [] hexByte = new Byte[2]{Convert.ToByte(100),  
        Convert.ToByte(50)};  
        myGroup.GroupNumber = hexByte;  
  
        DateTime myDate = new DateTime(2002,5,2);  
        myGroup.Today = myDate;  
  
        myGroup.PostitiveInt= "10000";  
        myGroup.IgnoreThis=true;  
        myGroup.Grouptype= GroupType.small;  
        Car thisCar =(Car)  myGroup.myCar("1234566");  
  
        // Serializes the class and closes the TextWriter.  
        overRideSerializer.Serialize(writer, myGroup);  
         writer.Close();  
    }  
  
    public void DeserializeOriginal(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlTypeMapping myMapping =   
        (new SoapReflectionImporter().ImportTypeMapping(  
        typeof(Group)));  
        XmlSerializer mySerializer =    
        new XmlSerializer(myMapping);  
  
        TextReader reader = new StreamReader(filename);  
  
        // Deserializes and casts the object.  
        Group myGroup;   
        myGroup = (Group) mySerializer.Deserialize(reader);  
  
        Console.WriteLine(myGroup.GroupName);  
        Console.WriteLine(myGroup.GroupNumber[0]);  
        Console.WriteLine(myGroup.GroupNumber[1]);  
        Console.WriteLine(myGroup.Today);  
        Console.WriteLine(myGroup.PostitiveInt);  
        Console.WriteLine(myGroup.IgnoreThis);  
        Console.WriteLine();  
    }  
  
    public void DeserializeOverride(string filename)  
    {  
        // Creates an instance of the XmlSerializer class.  
        XmlSerializer overRideSerializer = CreateOverrideSerializer();  
        // Reading the file requires a TextReader.  
        TextReader reader = new StreamReader(filename);  
  
        // Deserializes and casts the object.  
        Group myGroup;   
        myGroup = (Group) overRideSerializer.Deserialize(reader);  
  
        Console.WriteLine(myGroup.GroupName);  
        Console.WriteLine(myGroup.GroupNumber[0]);  
        Console.WriteLine(myGroup.GroupNumber[1]);  
        Console.WriteLine(myGroup.Today);  
        Console.WriteLine(myGroup.PostitiveInt);  
        Console.WriteLine(myGroup.IgnoreThis);  
    }  
  
    private XmlSerializer CreateOverrideSerializer()  
    {  
        SoapAttributeOverrides mySoapAttributeOverrides =   
        new SoapAttributeOverrides();  
        SoapAttributes soapAtts = new SoapAttributes();  
  
        SoapElementAttribute mySoapElement = new SoapElementAttribute();  
        mySoapElement.ElementName = "xxxx";  
        soapAtts.SoapElement = mySoapElement;  
        mySoapAttributeOverrides.Add(typeof(Group), "PostitiveInt",   
        soapAtts);  
  
        // Overrides the IgnoreThis property.  
        SoapIgnoreAttribute myIgnore = new SoapIgnoreAttribute();  
        soapAtts = new SoapAttributes();  
        soapAtts.SoapIgnore = false;        
        mySoapAttributeOverrides.Add(typeof(Group), "IgnoreThis",   
        soapAtts);  
  
        // Overrides the GroupType enumeration.  
        soapAtts = new SoapAttributes();  
        SoapEnumAttribute xSoapEnum = new SoapEnumAttribute();  
        xSoapEnum.Name = "Over1000";  
        soapAtts.SoapEnum = xSoapEnum;  
  
        // Adds the SoapAttributes to the   
        // mySoapAttributeOverridesrides.  
        mySoapAttributeOverrides.Add(typeof(GroupType), "large",   
        soapAtts);  
  
        // Creates a second enumeration and adds it.  
        soapAtts = new SoapAttributes();  
        xSoapEnum = new SoapEnumAttribute();  
        xSoapEnum.Name = "ZeroTo1000";  
        soapAtts.SoapEnum = xSoapEnum;  
        mySoapAttributeOverrides.Add(typeof(GroupType), "small",   
        soapAtts);  
  
        // Overrides the Group type.  
        soapAtts = new SoapAttributes();  
        SoapTypeAttribute soapType = new SoapTypeAttribute();  
        soapType.TypeName = "Team";  
        soapAtts.SoapType = soapType;  
        mySoapAttributeOverrides.Add(typeof(Group),soapAtts);  
  
        // Creates an XmlTypeMapping that is used to create an instance   
        // of the XmlSerializer class. Then returns the XmlSerializer.  
        XmlTypeMapping myMapping = (new SoapReflectionImporter(  
        mySoapAttributeOverrides)).ImportTypeMapping(typeof(Group));  
  
        XmlSerializer ser = new XmlSerializer(myMapping);  
        return ser;  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="18712-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18712-123">See Also</span></span>  
 <span data-ttu-id="18712-124">[Serialização XML e SOAP](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="18712-124">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span></span>  
 <span data-ttu-id="18712-125">[Atributos que controlam a serialização SOAP codificada](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="18712-125">[Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) </span></span>  
 <span data-ttu-id="18712-126">[Serialização XML com Serviços Web XML](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md) </span><span class="sxs-lookup"><span data-stu-id="18712-126">[XML Serialization with XML Web Services](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md) </span></span>  
 <span data-ttu-id="18712-127">[Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="18712-127">[How to: Serialize an Object](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span></span>  
 <span data-ttu-id="18712-128">[Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="18712-128">[How to: Deserialize an Object](../../../docs/standard/serialization/how-to-deserialize-an-object.md) </span></span>  
 [<span data-ttu-id="18712-129">Como serializar um objeto como um fluxo XML codificado para SOAP</span><span class="sxs-lookup"><span data-stu-id="18712-129">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
