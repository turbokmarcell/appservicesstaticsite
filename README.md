# Statikus Weboldal Hostolása Azure App Services-en
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

- Az Azure portál keresőjébe írd be az App Services kifejezést, a szolgáltatás megkereséséhez. <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRnLhoOuv9e7NLuruhd4L9hiGRkVF0KGxlIJA&s" alt="Kép leírása" width="25" />

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
  - GitHub Account: Társítsd a GitHub fiókodat a szolgáltatáshoz, majd válaszd ki a megfelelő Organization, Repository és Branch-et (CI/CD)

Build Details:
  - Build Presets: Autómatikusan felismeri a szolgáltatás (Custom (detected)
  - App location: Válaszd ki a projekted fő mappáját (Például, ha az alkalmazásod a root (gyökér) mappában található, akkor itt a / (perjel) lesz a válasz.)
  - Api location: Válaszd ki az API lokációját (Ha az alkalmazásod API-t is tartalmaz (pl. egy külön API mappát vagy function-okat), akkor itt adhatod meg a mappa nevét.)
  - Output location: Válaszd ki a Build kimeneteli helyét (Lehet üresen is hagyni)
  
App Service létrehozása:

  - Kattints a Review + Create gombra, ellenőrizd a beállításokat, és végül kattints a Create gombra.


## 2. App Service működésének tesztelése
- Miután rákattintottál a Creat gombra, navigálj az Azure portál bal felső sarkában található "*Microsoft Azure*" feliratra, és kattints rá
- A képernyő közepén látnod kell a létrehozott erőforrásokat(Resources) és látnod kell az általad létrehozott Static Web App nevét (A nevet a **Static Web App details** lépésnél adtad meg.)
- A névre kattintva a képernyő közepén található "Essentials" menüpontban  óaz URL mellett megtalálható lesz az általad hostolt statikus weboldal URL címe. Arra kattntva egy külön oldalon megnyílik az oldalad
-    **(Előfordulhat, hogy kell egy kis idő, míg az Azure szolgáltatás megtalálja a GitHub reposit, és megjeleníti a weboldalt)**

Mivel az Azure App Services rendelkezik beépített CI/CD integrációval, minden egyes új commit a GitHub repository-ban automatikusan deployolásra kerül az Azure-ra.
Az App Service monitorozza a repository-t, és bármely új változtatás automatikusan alkalmazásra kerül.
### 3. Weboldal elérhetősége
Miután a telepítés sikeres, az alkalmazás elérhető lesz az Azure által biztosított URL-en:

arduino
Copy code
https://<app-name>.azurewebsites.net
Itt fog megjelenni a statikus weboldalad.

![Kép leírása](https://media.istockphoto.com/id/1176972501/hu/fot%C3%B3/boldogtalan-k%C3%B3bor-kutya-szomor%C3%BA-szemmel-a-v%C3%A1ros-utc%C3%A1j%C3%A1n.jpg?s=2048x2048&w=is&k=20&c=sYXvfqJ7kfCiZBSenIrHqRXw5vZ3bUcBr77fBnWEy64=)
<img src="https://media.istockphoto.com/id/1176972501/hu/fot%C3%B3/boldogtalan-k%C3%B3bor-kutya-szomor%C3%BA-szemmel-a-v%C3%A1ros-utc%C3%A1j%C3%A1n.jpg?s=2048x2048&w=is&k=20&c=sYXvfqJ7kfCiZBSenIrHqRXw5vZ3bUcBr77fBnWEy64=" alt="Kép leírása" width="300" />
