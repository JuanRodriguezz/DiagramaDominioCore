---
title: "ERMX - Client Domain.  Version: Version 1"
date: 2025-03-12 12:53:24 p.m.
cambios: Client.ClientType ( persona física o moral) & ProducDesgin 
config:
  theme: base
---

erDiagram
    Client ||--|{ Card : DomainRelation

    Client {
        int DocumentIdentifier
        string LegacyIdentifier
        int BranchIdentifier
        int GroupIdentifier
        int ClientIdentifier
        string Name 
        string RFC
        string Telephone
        date InsertedDate	
        string StatusClient
        string ClientType_Moral_Fisica
        int BankIdentifier
        int BankName
        string[] Address
        string[] Design
        string[] ClientSettings
        string[] Product
    }

    Client }|..|| Contract : has
    Contract {
        int PaymentTerm_PendienteValidar
    }

    Client }|..|| Address : has
    Address {
        int AddressIdentifier
        string Street
        string Neighborhood
        string State
        string City
        string ZipCode
        string CountryCode
        string Code
        string SpecialCode
        int AddressTypeId
        string AddressTypeDescription
        string NameContact
        string ContactTelephone
    }
    Client }|..|| ClientSettings : has
    ClientSettings {
        int     ClientSettingsIdentifier
        string  Deductible
        int     EmissionTypeIdentifier
        string  EmissionTypeDescription
        int ClientProcessIdentifier
        string ClientProcessName
        string[] DefaultSettings
        string[] ProductSettings
        string[] DetailSettingsSettings
     }
    ClientSettings }|..|{DefaultSettings : has
    DefaultSettings {
        int DefaultSettingsIdentifier
        string NameSetting
        string SettingType
        string Code
        string Value
        string Level
        string PersistanceUser
        bit IsActive       
        date InsertedDate
    }
    ClientSettings }|..|{ ProductSettings : has
    ProductSettings {
        decimal ProductSettingIdentifier
        string Process
        string NameSetting
        string Code
        string Value
        string Level
        string PersistanceUser
        bit Deductible
        bit IsActive       
        date InsertedDate
        string ProductIdentifier
    }
     ClientSettings}|..|{ ClientProcess: has
    UserAuthorization }|..|{ ClientProcess : has
    ClientProcess {
        int ClientProcessIdentifier
        sting ClientProcessName
        bit IsActive
        date ProcessCreateDate
        date ProcessModifiedDate
     }
     
    Product }|..|{UserAuthorization  : has
    Client }|..|{ UserAuthorization : has
    ClientRoleSettings }|..|{ UserAuthorization : has
      UserAuthorization {
        int UserAuthorizationIdentifier
        bigint ClientIdentification
        int  ClientProcessIdentifier
        int  ClientProcessName
        smallint StatusProcessIntegrationIdentification
        string BusinessName
        int ProductIdentifier
        date ProcessDate
        int ProductIdentifier
        string[] ClientRoleSettingIdentifier        
    }

    ClientRoleSettings {
        int ClientRoleSettingIdentifier
        string Username
        string Role
        string Email
        string Telephone
    }

    Client }|..|{ Design : has
    Design {
        int DesignIdentifier
        string Code
        string DesignDescription
        bit IsDefault
        bit IsActive
        string AuthorizingDesign
        smallint ExternalIdentifier
    }

    Client }|..|{ Product : has
    Product {
        int ProductIdentifier
        string ProductName
         string Family
        string  GroupName
        string  GroupNameDescription
        bit IsActive
        string[] ProductDesign
        string[] Authorizer
    }

    Product }|..|{Authorizer : has
    Authorizer {
        int ProductAuthorizerIdentifier
        string Description
        bit IsActive
        date CreatedDate
    }

    Product }|..|{ProductDesign : has
    ProductDesign {
        int ProductDesignIdentifier
        string DesignCode
        string DesignDescription
        string AuthorizingDesign 
        string DesignsCodeExternal
        sting FlyerCode
        string PacketCode
        int CardProfile
        string CardCarrierCode
        bit IsActiveCardCarrierCode
        bit IsActiveProductDesign
        date CreatedDate
    }

    Product }|..|{ ProductSettings : has
    Client }|..|{ Log : has
    Log }|..|{ User : has 
    Log {
        decimal LogIdentifier
        
        string ProcessName
        string ErrorType
        date InsertDate
        string AlertType
        String Message
        int ProductId_Pendiente
        string[] Client
    }

        Card }|..|{ CardProfile : has

    Card {
        string CardIdentifier
        string AccountProfile
        int ProductId
        string Description
        decimal CreditLimit
        iint CardProfileIdentifier
        string[] CurrentAccountStatus
        string[] UseExpirationBalance
        
    }


    Product }|..|{ CardProfile : has
    CardProfile {
        int CardProfileIdentifier
        string CardProfile
        int ProductId
        int Csnprefix
        string BinSegment
        decimal Description
       
    }


    Order {
        string[] Products
        bigint OrderNumber
        decimal CreditLimit
        decimal Amount
        string[] CurrentAccountStatus
        string[] UseExpirationBalance
    }

    Product }|..|{ testJuanito : has
    testJuanito         {
        int testjuanitoId 
    }

 
    Client ||--|{ User : DomainRelation
    Card }|..|{ Product : has
    Card }|..|{ Order : has
 
