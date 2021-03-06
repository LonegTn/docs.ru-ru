---
title: Упрощенная конфигурация
description: Подробнее о упрощенной настройке служб WCF. .NET Framework 4.6.1 предоставляет способ уменьшения размера и сложности конфигурации службы.
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 248fe05e5854dbbec1a66b046c4def3d11d30327
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235952"
---
# <a name="simplified-configuration"></a>Упрощенная конфигурация

Настройка служб Windows Communication Foundation (WCF) может быть сложной задачей. Разных параметров много, и не всегда легко понять, какие настройки необходимы. Хотя файлы конфигурации увеличивают гибкость служб WCF, они также являются источником для многих трудностей при обнаружении проблем. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] устраняет эти проблемы, предоставляя способ уменьшить размер и упростить конфигурацию службы.  
  
## <a name="simplified-configuration"></a>Упрощенная конфигурация  

 В файлах конфигурации службы WCF `system.serviceModel` раздел <> содержит `service` элемент <> для каждой размещенной службы. `service`Элемент> <содержит коллекцию `endpoint` элементов <>, которые указывают конечные точки, предоставляемые для каждой службы, и, при необходимости, набор поведений службы. <`endpoint`> элементы указывают адрес, привязку и контракт, предоставляемые конечной точкой, и при необходимости привязку конфигурации и поведения конечной точки. В `system.serviceModel` разделе <> также содержится элемент <`behaviors`>, который позволяет указать поведение службы или конечной точки. В следующем примере показан раздел <`system.serviceModel`> файла конфигурации.  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] упрощает настройку службы WCF путем удаления требования к `service` элементу> <. Если вы не добавите <`service`> или добавите конечные точки в раздел <`service`> и ваша служба не определит конечные точки программными средствами, в службу автоматически добавляется набор конечных точек по умолчанию, по одной для каждого базового адреса службы и для каждого контракта, реализованного службой. В каждой из этих конечных точек адрес конечной точки соответствует базовому адресу, привязка определяется схемой базового адреса, а контракт - службой. Если не нужно задавать конечные точки или поведения служб или изменять какие-либо параметры привязки, то указывать файл конфигурации служб не нужно вообще. Если служба реализует два контракта, а на узле включен транспорт по протоколам HTTP и TCP, то узел службы создаст четыре точки по умолчанию: по одной на каждый контракт для каждого транспорта. Чтобы создать по умолчанию конечные точки, узел службы должен знать, какие привязки использовать. Эти параметры указываются в разделе <`protocolMappings`> в `system.serviceModel` разделе <>. Раздел <`protocolMappings`> содержит список схем транспортного протокола, сопоставленных с типами привязки. Узел службы использует переданные ему базовые адреса, чтобы определить, какую привязку использовать. В следующем примере используется `protocolMappings` элемент> <.  
  
> [!WARNING]
> Изменение элементов конфигурации по умолчанию, например привязок или поведений, может повлиять на службы, определенные на нижних уровнях иерархии конфигурации, поскольку они могут использовать эти привязки или поведения. Поэтому пользователь, изменяющий привязки и поведения по умолчанию, должен знать, что эти изменения могут повлиять на другие службы в иерархии.  
  
> [!NOTE]
> Службы, размещенные в службах IIS или WAS, используют в качестве базового адреса виртуальный каталог.  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 В предыдущем примере конечная точка с базовым адресом, начинающимся с «http», использует привязку <xref:System.ServiceModel.BasicHttpBinding>. Конечная точка с базовым адресом, начинающимся с «net.tcp», использует привязку <xref:System.ServiceModel.NetTcpBinding>. Параметры можно переопределить в локальном файле App.config или Web.config.  
  
 Каждый элемент в разделе <`protocolMappings`> должен указывать схему и привязку. При необходимости можно указать `bindingConfiguration` атрибут, задающий конфигурацию привязки в `bindings` разделе <> файла конфигурации. Если параметры `bindingConfiguration` не заданы, то используется анонимная конфигурация привязки нужного типа.  
  
 Поведение службы настраивается для конечных точек по умолчанию с помощью анонимных <`behavior`> разделов в <`serviceBehaviors`> разделах. Для настройки поведения службы используются любые неименованные <`behavior` элементы> в <`serviceBehaviors`>. Например, следующий файл конфигурации позволяет публиковать метаданные всех служб в узле.  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 Поведения конечных точек настраиваются с помощью анонимных <`behavior`> разделов в <`serviceBehaviors`> разделах.  
  
 В следующем примере приведен файл конфигурации, эквивалентный файлу, приведенному в начале данного раздела, с упрощенной моделью конфигурации.  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
> Эта возможность относится только к конфигурации службы WCF, а не к конфигурации клиента. В большинстве случаев конфигурация клиента WCF создается с помощью средства, например svcutil.exe, или путем добавления ссылки на службу из Visual Studio. При ручной настройке клиента WCF необходимо добавить \<client> элемент в конфигурацию и указать все конечные точки, которые необходимо вызвать.  
  
## <a name="see-also"></a>См. также

- [Настройка служб с использованием файлов конфигурации](configuring-services-using-configuration-files.md)
- [Настройка привязок для служб](configuring-bindings-for-wcf-services.md)
- [Настройка привязок, предоставляемых системой](./feature-details/configuring-system-provided-bindings.md)
- [Настройка служб](configuring-services.md)
- [Настройка служб WCF](configuring-services.md)
- [Настройка служб WCF в коде](configuring-wcf-services-in-code.md)
