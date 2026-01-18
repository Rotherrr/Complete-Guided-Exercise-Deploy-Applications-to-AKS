# Complete-Guided-Exercise-Deploy-Applications-to-AKS
Projekt stworzony na zajęcia WSB-NLU

Azure Container Registry - data 

| Settings | Value |
| :--- | :--- |
| Resource Group | acr-01-RG |
| Registry Name | wbnluromanczyzycki | 
| Region | francecentral | 
| Availability zone | None | 
| SKU | Basic| 


Virtual Network
| Settings | Value | 
| :--- | :--- | 
| Resource Group | acr-01-RG |
| Virtual network name | vnet-01 |
| Region | francecentral | 


# Sprawozdanie – AKS + ACR

## 1. Zakres ćwiczenia
- ACR: utworzenie i integracja z AKS
- AKS: Linux + Windows node pools
- Deployment aplikacji kontenerowych
- Weryfikacja i cleanup

## 2. Architektura (stan końcowy)
| Komponent | Konfiguracja |
|--------|-------------|
| ACR | Basic, francecentral |
| AKS | Azure CNI |
| Linux node pool | 2 × B4ms |
| Windows node pool | 2 × B4ms |
| VNET | 10.0.0.0/16 |
| Subnet AKS | 10.0.0.0/20 |

## 3. Obrazy kontenerowe
| Image | OS | Runtime | Registry |
|----|----|--------|--------|
| hellofromnode:v1.0 | Linux | Node.js 20 | ACR |
| hellofromdotnet:v1.0 | Windows | .NET 7 | ACR |

## 4. Kubernetes
- Namespaces: dev-node, dev-dotnet
- nodeSelector: linux / windows
- Services: LoadBalancer

## 5. Weryfikacja
- Deployment status: OK
- External IP: OK
- Dostęp HTTP: OK

## 6. Wnioski techniczne
- Windows node pool ⇒ Azure CNI
- ACR Tasks ⇒ brak lokalnego Dockera
