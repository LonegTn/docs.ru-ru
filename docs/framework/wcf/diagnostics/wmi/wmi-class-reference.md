---
title: Справочные сведения по классам WMI
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 9830fbf50e8df625e3d3077a66c66e0370204acb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262259"
---
# <a name="wmi-class-reference"></a>Справочные сведения по классам WMI

В этом разделе перечислены все классы WMI, предоставляемые поставщиком WMI для Windows Communication Foundation (WCF).  
  
## <a name="accessing-wmi-instances"></a>Доступ к экземплярам WMI  

 Все классы, перечисленные в ссылках на объект WMI, невозможно создать напрямую, за исключением классов службы, домена приложения, контракта, ServiceToEndpointAssociation и конечной точки. Чтобы получить доступ к другим экземплярам, можно получить доступ к свойствам указанных выше классов верхнего уровня. Например, можно получить доступ к экземпляру TransportBindingElement из экземпляра конечной точки — > Binding-> BindingElements.  
  
## <a name="in-this-section"></a>в этом разделе  

 [ActivityTransfer](activitytransfer.md)  
  
 [AppDomainInfo](appdomaininfo.md)  
  
 [AspNetCompatibilityRequirementsAttribute](aspnetcompatibilityrequirementsattribute.md)  
  
 [AsymmetricSecurityBindingElement](asymmetricsecuritybindingelement.md)  
  
 "Класс поведения"  
  
 [BinaryMessageEncodingBindingElement](binarymessageencodingbindingelement.md)  
  
 [Привязка](binding.md)  
  
 [BindingElement](bindingelement.md)  
  
 [CallbackBehavior](callbackbehavior.md)  
  
 [Класс Channel](channel-class.md)  
  
 [ChannelPoolSettings](channelpoolsettings.md)  
  
 [ClientCredentials](clientcredentials.md)  
  
 [ClientViaBehavior](clientviabehavior.md)  
  
 [CompositeDuplexBindingElement](compositeduplexbindingelement.md)  
  
 [ConnectionOrientedTransportBindingElement](connectionorientedtransportbindingelement.md)  
  
 [Архивирован](contract.md)  
  
 [CustomBindingElement](custombindingelement.md)  
  
 [DeliveryRequirementsAttribute](deliveryrequirementsattribute.md)  
  
 [Конечная точка](endpoint.md)  
  
 [HttpsTransportBindingElement](httpstransportbindingelement.md)  
  
 [HttpTransportBindingElement](httptransportbindingelement.md)  
  
 [LocalServiceSecuritySettings](localservicesecuritysettings.md)  
  
 [MatchAllEndpointBehavior](matchallendpointbehavior.md)  
  
 [MessageEncodingBindingElement](messageencodingbindingelement.md)  
  
 [MsmqBindingElementBase](msmqbindingelementbase.md)  
  
 [MsmqIntegrationBindingElement](msmqintegrationbindingelement.md)  
  
 [MsmqTransportBindingElement](msmqtransportbindingelement.md)  
  
 [MtomMessageEncodingBindingElement](mtommessageencodingbindingelement.md)  
  
 [MustUnderstandBehavior](mustunderstandbehavior.md)  
  
 [NamedPipeConnectionPoolSettings](namedpipeconnectionpoolsettings.md)  
  
 [NamedPipeTransportBindingElement](namedpipetransportbindingelement.md)  
  
 [OneWayBindingElement](onewaybindingelement.md)  
  
 "Класс операции"  
  
 [OperationBehaviorAttribute](operationbehaviorattribute.md)  
  
 [PeerCustomResolverBindingElement](peercustomresolverbindingelement.md)  
  
 [PeerResolverBindingElement](peerresolverbindingelement.md)  
  
 [PeerSecuritySettings](peersecuritysettings.md)  
  
 [PeerTransportBindingElement](peertransportbindingelement.md)  
  
 [PeerTransportSecuritySettings](peertransportsecuritysettings.md)  
  
 [PnrpPeerResolverBindingElement](pnrppeerresolverbindingelement.md)  
  
 [PrivacyNoticeBindingElement](privacynoticebindingelement.md)  
  
 [ReliableSessionBindingElement](reliablesessionbindingelement.md)  
  
 [SecurityBindingElement](securitybindingelement.md)  
  
 [Служба](service.md)  
  
 [ServiceAppDomain](serviceappdomain.md)  
  
 [ServiceAuthorizationBehavior](serviceauthorizationbehavior.md)  
  
 [ServiceBehaviorAttribute](servicebehaviorattribute.md)  
  
 [ServiceCredentials](servicecredentials.md)  
  
 [ServiceDebugBehavior](servicedebugbehavior.md)  
  
 [ServiceMetadataBehavior](servicemetadatabehavior.md)  
  
 [ServiceSecurityAuditBehavior](servicesecurityauditbehavior.md)  
  
 [ServiceThrottlingBehavior](servicethrottlingbehavior.md)  
  
 [ServiceTimeoutsBehavior](servicetimeoutsbehavior.md)  
  
 [ServiceToEndpointAssociation](servicetoendpointassociation.md)  
  
 [SslStreamSecurityBindingElement](sslstreamsecuritybindingelement.md)  
  
 [SymmetricSecurityBindingElement](symmetricsecuritybindingelement.md)  
  
 [SynchronousReceiveBehavior](synchronousreceivebehavior.md)  
  
 [TcpConnectionPoolSettings](tcpconnectionpoolsettings.md)  
  
 [TcpTransportBindingElement](tcptransportbindingelement.md)  
  
 [TextMessageEncodingBindingElement](textmessageencodingbindingelement.md)  
  
 [TraceListener](tracelistener.md)  
  
 [TraceListenerArgument](tracelistenerargument.md)  
  
 [TransactedBatchingBehavior](transactedbatchingbehavior.md)  
  
 [TransactionFlowAttribute](transactionflowattribute.md)  
  
 [TransactionFlowBindingElement](transactionflowbindingelement.md)  
  
 [TransportBindingElement](transportbindingelement.md)  
  
 [TransportSecurityBindingElement](transportsecuritybindingelement.md)  
  
 [UseManagedPresentationBindingElement](usemanagedpresentationbindingelement.md)  
  
 [WindowsStreamSecurityBindingElement](windowsstreamsecuritybindingelement.md)  
  
 [WSAT_TraceEvent](wsat-traceevent.md)  
  
 [WSAT_TraceProvider](wsat-traceprovider.md)  
  
 [WSAT_TraceRecord](wsat-tracerecord.md)  
  
 [XmlDictionaryReaderQuotas](xmldictionaryreaderquotas.md)  
  
 [XmlSerializerOperationBehavior](xmlserializeroperationbehavior.md)
