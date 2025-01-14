# Statikus Weboldal Hostolása Azure App Services-en (hu)
Ez a projekt bemutatja, hogyan lehet létrehozni és hosztolni egy statikus weboldalt az Azure App Services segítségével. Az alkalmazás GitHub repository-ból kerül automatikusan telepítésre, folyamatos integrációval (CI/CD), hogy a weboldal frissítései és módosításai gyorsan alkalmazásra kerüljenek.

## Projekt célja:
  A célja annak bemutatása, hogyan lehet egy statikus weboldalt egyszerűen és hatékonyan üzemeltetni Azure-ban, a GitHub folyamatos integrációs rendszerét (CI/CD) felhasználva, hogy automatikusan frissítse a weboldalt minden egyes módosításnál.

### Előfeltételek
Mielőtt elkezdenéd a projektet, győződj meg róla, hogy rendelkezel az alábbiakkal:

- Azure fiók: Ha még nincs, hozz létre egyet [itt](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account/search?icid=free-search&ef_id=_k_EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE_k_&OCID=AIDcmmip7xznjm_SEM__k_EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE_k_&gad_source=1&gclid=EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE).
- GitHub fiók: Regisztrálj, ha még nem tetted meg, [itt](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).
- Visual Studio Code vagy más szövegszerkesztő.
- Git telepítve a gépeden.

## 1. Azure App Service Létrehozása

Nyisd meg az Azure Portal-t, és jelentkezz be a fiókoddal.

**App Service létrehozása:**

- Az Azure portál keresőjébe írd be az App Services kifejezést, a szolgáltatás megkereséséhez. <img src="/assets/images.jpg" alt="Kép leírása" width="25" />

- Kattints az + Create gombra az új alkalmazás létrehozásához, majd válaszd a + Static Web App a statikus weboldal hostolásához használandó funkciót.
  
*Töltsd ki az alábbi mezőket:*

Project Details:
  - Subscription: Válaszd ki a megfelelő előfizetést.
  - Resource Group: Válassz vagy hozz létre egy új resource group-ot.
    
Static Web App details:
  - Name: Add meg az alkalmazás nevét (pl. my-static-website).
    
Hosting plan:
  - Plan Type: Válaszd ki a megfelelő hoszting tervet (pl.Free: For hobby or personal projects)
    
Deployment details:
  - Source: Válaszd ki, hogy honnan integrálja be az App Services a weboldal kódjait (Érdemes a GitHubot választani)
  - GitHub Account: Társítsd a GitHub fiókodat a szolgáltatáshoz, majd válaszd ki a megfelelő Organization, Repository és Branch-et :green_circle:(CI/CD)

Build Details:
  - Build Presets: Autómatikusan felismeri a szolgáltatás (Custom (detected)
  - App location: Válaszd ki a projekted fő mappáját (Például, ha az alkalmazásod a root (gyökér) mappában található, akkor itt a / (perjel) lesz a válasz.)
  - Api location: Válaszd ki az API lokációját (Ha az alkalmazásod API-t is tartalmaz (pl. egy külön API mappát vagy function-okat), akkor itt adhatod meg a mappa nevét.)
  - Output location: Válaszd ki a Build kimeneteli helyét (Lehet üresen is hagyni)
  
App Service létrehozása:

  - Kattints a Review + Create gombra, ellenőrizd a beállításokat, és végül kattints a Create gombra.


## 2. App Service működésének tesztelése
- Miután rákattintottál a Creat gombra, navigálj az Azure portál bal felső sarkában található "*Microsoft Azure*" feliratra, és kattints rá
- A képernyő közepén látnod kell a létrehozott erőforrásokat(Resources) és látnod kell az általad létrehozott Static Web App nevét (A nevet a **Static Web App details** lépésnél adtad meg.)<img src="/assets/Opera Pillanatfelvétel_2025-01-13_161646_portal.azure.com.png" alt="Kép leírása" width="1500" />
- A névre kattintva a képernyő közepén található "Essentials" menüpontban  óaz URL mellett megtalálható lesz az általad hostolt statikus weboldal URL címe. Arra kattntva egy külön oldalon megnyílik az oldalad <img src="/assets/Opera Pillanatfelvétel_2025-01-13_161253_portal.azure.com.png" alt="Kép leírása" width="1500" />
  :red_circle:Előfordulhat, hogy kell egy kis idő, míg az Azure szolgáltatás megtalálja a GitHub reposit, és megjeleníti a weboldalt

Mivel az Azure App Services rendelkezik beépített CI/CD integrációval, minden egyes új commit a GitHub repository-ban automatikusan deployolásra kerül az Azure-ra.
Az App Service monitorozza a repository-t, és bármely új változtatás automatikusan alkalmazásra kerül.

## Azure Telepítési Konfiguráció
Az `azure_deployment.json` fájl tartalmazza a projekthez tartozó JSON fájlt. Ez magában foglalja az összes erőforrást és konfigurációt, amelyet a statikus weboldal Azure App Services-re történő telepítéséhez használtunk.


# Hosting a Static Website on Azure App Services (eng)
This project demonstrates how to create and host a static website using Azure App Services. The application is automatically deployed from a GitHub repository with continuous integration (CI/CD), ensuring that updates and changes to the website are quickly applied.

## Project Goal:
The goal is to demonstrate how to easily and efficiently host a static website on Azure, using GitHub’s continuous integration system (CI/CD) to automatically update the website with each change.

### Prerequisites
Before starting the project, ensure you have the following:

- Azure Account: If you don’t have one yet, create one [here](https://azure.microsoft.com/en-us/pricing/purchase-options/azure-account/search?icid=free-search&ef_id=_k_EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE_k_&OCID=AIDcmmip7xznjm_SEM__k_EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE_k_&gad_source=1&gclid=EAIaIQobChMIop6rouryigMVJZGDBx1y3CuNEAAYASAAEgLWsPD_BwE).
- GitHub Account: Register if you haven’t already [here](https://github.com/signup?ref_cta=Sign+up&ref_loc=header+logged+out&ref_page=%2F&source=header-home).
- Visual Studio Code or another text editor.
- Git installed on your machine.
- 
## 1. Creating the Azure App Service

Open the Azure Portal and sign in with your account.

**Creating the App Service:**

- In the Azure portal’s search bar, type "App Services" to find the service. <img src="/assets/images.jpg" alt="Image description" width="25" />
- Click the + Create button to create a new application, then select the + Static Web App option to host a static website.

*Fill in the following fields:*

Project Details:
- Subscription: Choose the appropriate subscription.
- Resource Group: Select or create a new resource group.
  
Static Web App details:
- Name: Enter the application name (e.g., my-static-website).
- Hosting plan: Plan Type: Select the appropriate hosting plan (e.g., Free: For hobby or personal projects).
  
Deployment details:
- Source: Choose where the App Services should integrate the website’s code (It’s recommended to choose GitHub).
- GitHub Account: Link your GitHub account to the service, then select the appropriate Organization, Repository, and Branch :green_circle:(CI/CD).
  
Build Details:
- Build Presets: Automatically detected by the service (Custom (detected)).
- App location: Choose your project’s main folder (For example, if your app is located in the root folder, enter / here).
- Api location: Choose the API location (If your app includes an API, such as a separate API folder or functions, specify the folder name here).
- Output location: Choose the Build output location (can be left empty).
  
Creating the App Service:
- Click Review + Create, review the settings, and then click Create.
  
## 2. Testing the App Service
- After clicking the Create button, navigate to the "Microsoft Azure" link in the upper left corner of the Azure portal and click on it.
- In the middle of the screen, you should see the created resources (Resources), and the Static Web App name you provided (from the Static Web App details step) should appear. <img src="/assets/Opera Pillanatfelvétel_2025-01-13_161646_portal.azure.com.png" alt="Image description" width="1500" />
- Click on the name, and in the "Essentials" section in the middle of the screen, you’ll find the URL for the static website you’ve hosted. Clicking on the URL will open your site in a new page. <img src="/assets/Opera Pillanatfelvétel_2025-01-13_161253_portal.azure.com.png" alt="Image description" width="1500" />
:red_circle: It may take some time for the Azure service to locate the GitHub repository and display the website.
Since Azure App Services includes built-in CI/CD integration, every new commit in the GitHub repository will automatically be deployed to Azure. The App Service monitors the repository, and any new changes are automatically applied.

## Azure Deployment Configuration
The file `azure_deployment.json` contains the JSON file for this project. It includes all the resources and configurations used to deploy the static website on Azure App Services
