# 👻 Ghost Sigurnosni Modul
**PowerShell-baziran alat za učvršćavanje sigurnosti Windows i Azure sustava**

> **Proaktivno učvršćavanje sigurnosti za Windows krajnje točke i Azure okruženja.** Ghost pruža PowerShell-bazirane funkcije učvršćavanja koje mogu pomoći u smanjenju uobičajenih vektora napada onemogućavanjem nepotrebnih usluga i protokola.

## ⚠️ Važna odricanja

**TESTIRANJE JE POTREBNO**: Uvijek testirajte Ghost u ne-produkcijskim okruženjima prvo. Onemogućavanje usluga može utjecati na legitimne poslovne funkcije.

**NEMA JAMSTAVA**: Iako Ghost cilja na uobičajene vektore napada, nijedan sigurnosni alat ne može spriječiti sve napade. Ovo je jedna komponenta sveobuhvatne sigurnosne strategije.

**OPERACIJSKI UTJECAJ**: Neke funkcije mogu utjecati na funkcionalnost sustava. Pažljivo pregledajte svaku postavku prije implementacije.

**PROFESIONALNA PROCJENA**: Za produkcijska okruženja savjetujte se sa sigurnosnim stručnjacima kako biste osigurali da postavke odgovaraju potrebama vaše organizacije.

## 📊 Sigurnosni krajolik

Štete od ransomware dosegnule su **57 milijardi dolara u 2025.**, a istraživanja pokazuju da mnogi uspješni napadi iskorištavaju osnovne Windows usluge i pogrešne konfiguracije. Uobičajeni vektori napada uključuju:

- **90% ransomware incidenata** uključuje iskorištavanje RDP-a
- **SMBv1 ranjivosti** omogućile su napade poput WannaCry i NotPetya
- **Makroi dokumenata** ostaju primarni način dostave malware-a
- **USB-bazirani napadi** nastavljaju ciljati zrakoprazne mreže
- **Zlouporaba PowerShell-a** značajno se povećala u posljednjim godinama

## 🛡️ Ghost sigurnosne funkcije

Ghost pruža **16 Windows funkcija učvršćavanja** plus **Azure sigurnosnu integraciju**:

### Učvršćavanje Windows krajnjih točaka

| Funkcija | Svrha | Razmatranja |
|----------|-------|-------------|
| `Set-RDP` | Upravlja pristupom udaljenom radnom stolu | Može utjecati na udaljenu administraciju |
| `Set-SMBv1` | Kontrolira zastarjeli SMB protokol | Potreban za vrlo stare sustave |
| `Set-AutoRun` | Kontrolira AutoPlay/AutoRun | Može utjecati na korisničku udobnost |
| `Set-USBStorage` | Ograničava USB uređaje za pohranu | Može utjecati na legitimnu USB uporabu |
| `Set-Macros` | Kontrolira izvršavanje Office makroa | Može utjecati na dokumente s omogućenim makroima |
| `Set-PSRemoting` | Upravlja PowerShell udaljenim povezivanjem | Može utjecati na udaljeno upravljanje |
| `Set-WinRM` | Kontrolira Windows Remote Management | Može utjecati na udaljenu administraciju |
| `Set-LLMNR` | Upravlja protokolom razrješavanja imena | Obično je sigurno za onemogućavanje |
| `Set-NetBIOS` | Kontrolira NetBIOS preko TCP/IP | Može utjecati na zastarjele aplikacije |
| `Set-AdminShares` | Upravlja administrativnim dijeljenjem | Može utjecati na udaljeni pristup datotekama |
| `Set-Telemetry` | Kontrolira prikupljanje podataka | Može utjecati na dijagnostičke sposobnosti |
| `Set-GuestAccount` | Upravlja gostujućim računom | Obično je sigurno za onemogućavanje |
| `Set-ICMP` | Kontrolira ping odgovore | Može utjecati na mrežnu dijagnostiku |
| `Set-RemoteAssistance` | Upravlja udaljenom pomoći | Može utjecati na rad helpdeska |
| `Set-NetworkDiscovery` | Kontrolira otkrivanje mreže | Može utjecati na pregledavanje mreže |
| `Set-Firewall` | Upravlja Windows Firewall | Kritično za mrežnu sigurnost |

### Azure Cloud sigurnost

| Funkcija | Svrha | Zahtjevi |
|----------|-------|----------|
| `Set-AzureSecurityDefaults` | Omogućava osnovnu Azure AD sigurnost | Microsoft Graph dozvole |
| `Set-AzureConditionalAccess` | Konfigurira pravila pristupa | Azure AD P1/P2 licenciranje |
| `Set-AzurePrivilegedUsers` | Provjerava privilegirane račune | Global Admin dozvole |

### Opcije enterprise implementacije

| Metoda | Slučaj korištenja | Zahtjevi |
|--------|------------------|----------|
| **Direktno izvršavanje** | Testiranje, mala okruženja | Lokalna admin prava |
| **Group Policy** | Domenske okruženja | Domain admin, GP upravljanje |
| **Microsoft Intune** | Cloud-upravljani uređaji | Intune licenciranje, Graph API |

## 🚀 Brzi početak

### Sigurnosna procjena
```powershell
# Učitajte Ghost modul
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1

# Provjerite trenutno sigurnosno stanje
Get-Ghost
```

### Osnovno učvršćavanje (prvo testirajte)
```powershell
# Osnovno učvršćavanje - prvo testirajte u laboratorijskom okruženju
Set-Ghost -SMBv1 -AutoRun -Macros

# Pregledajte promjene
Get-Ghost
```

### Enterprise implementacija
```powershell
# Group Policy implementacija (domenska okruženja)
Set-Ghost -SMBv1 -AutoRun -GroupPolicy

# Intune implementacija (cloud-upravljani uređaji)
Set-Ghost -SMBv1 -RDP -USBStorage -Intune
```

## 📋 Metode instalacije

### Opcija 1: Direktno preuzimanje (testiranje)
```powershell
Invoke-WebRequest 'https://raw.githubusercontent.com/jimrtyler/Ghost/main/Ghost.ps1' -OutFile .\Ghost.ps1
Get-Content .\Ghost.ps1
. .\Ghost.ps1
```

### Opcija 2: Instalacija modula
```powershell
# Instalirajte iz PowerShell Gallery (kada bude dostupno)
Install-Module Ghost -Scope CurrentUser
Import-Module Ghost
```

### Opcija 3: Enterprise implementacija
```powershell
# Kopirajte na mrežnu lokaciju za Group Policy implementaciju
# Konfigurirajte Intune PowerShell skripte za cloud implementaciju
```

## 💼 Primjeri slučajeva korištenja

### Mali biznis
```powershell
# Osnovna zaštita s minimalnim utjecajem
Set-Ghost -SMBv1 -AutoRun -Macros -ICMP
```

### Zdravstveno okruženje
```powershell
# HIPAA-usmjereno učvršćavanje
Set-Ghost -SMBv1 -RDP -USBStorage -AdminShares -Telemetry
```

### Financijske usluge
```powershell
# Konfiguracija visoke sigurnosti
Set-Ghost -RDP -SMBv1 -AutoRun -USBStorage -Macros -PSRemoting -AdminShares
```

### Cloud-First organizacija
```powershell
# Intune-upravljana implementacija
Connect-IntuneGhost -Interactive
Set-Ghost -SMBv1 -RDP -AutoRun -Macros -Intune
```

## 🔍 Detalji funkcija

### Osnovne funkcije učvršćavanja

#### Mrežne usluge
- **RDP**: Blokira pristup udaljenom radnom stolu ili randomizira port
- **SMBv1**: Onemogućava zastarjeli protokol dijeljenja datoteka
- **ICMP**: Sprječava ping odgovore za izvještavanje
- **LLMNR/NetBIOS**: Blokira zastarjele protokole razrješavanja imena

#### Sigurnost aplikacija
- **Makroi**: Onemogućava izvršavanje makroa u Office aplikacijama
- **AutoRun**: Sprječava automatsko izvršavanje s uklonjivog medija

#### Udaljeno upravljanje
- **PSRemoting**: Onemogućava PowerShell udaljene sesije
- **WinRM**: Zaustavlja Windows Remote Management
- **Remote Assistance**: Blokira veze udaljene pomoći

#### Kontrola pristupa
- **Admin Shares**: Onemogućava C$, ADMIN$ dijeljenja
- **Guest Account**: Onemogućava pristup gostujućem računu
- **USB Storage**: Ograničava korištenje USB uređaja

### Azure integracija
```powershell
# Povežite se na Azure tenant
Connect-AzureGhost -Interactive

# Omogućite sigurnosne zadane postavke
Set-AzureSecurityDefaults -Enable

# Konfigurirajte uvjetni pristup
Set-AzureConditionalAccess -BlockLegacyAuth -RequireMFA

# Provjerite privilegirane korisnike
Set-AzurePrivilegedUsers -AuditOnly
```

### Intune integracija (novo u v2)
```powershell
# Povežite se na Intune
Connect-IntuneGhost -Interactive

# Implementirajte putem Intune pravila
Set-IntuneGhost -Settings @{
    RDP = $true
    SMBv1 = $true
    USBStorage = $true
    Macros = $true
}
```

## ⚠️ Važna razmatranja

### Zahtjevi testiranja
- **Laboratorijsko okruženje**: Testirajte sve postavke u izoliranom okruženju prvo
- **Postupna implementacija**: Postupno implementirajte kako biste identificirali probleme
- **Plan vraćanja**: Osigurajte da možete vratiti promjene ako je potrebno
- **Dokumentacija**: Zabilježite koje postavke rade za vaše okruženje

### Mogući utjecaj
- **Produktivnost korisnika**: Neke postavke mogu utjecati na dnevne tijekove rada
- **Zastarjele aplikacije**: Stariji sustavi mogu zahtijevati određene protokole
- **Udaljeni pristup**: Razmotriti utjecaj na legitimnu udaljenu administraciju
- **Poslovni procesi**: Provjerite da postavke ne narušavaju kritične funkcije

### Sigurnosna ograničenja
- **Obrambena dubina**: Ghost je jedan sloj sigurnosti, ne potpuno rješenje
- **Kontinuirano upravljanje**: Sigurnost zahtijeva kontinuirano praćenje i ažuriranja
- **Korisnička edukacija**: Tehnički kontrole moraju biti uparene sa sigurnosnom sviješću
- **Evolucija prijetnji**: Novi načini napada mogu zaobići trenutnu zaštitu

## 🎯 Primjeri scenarija napada

Dok Ghost cilja na uobičajene vektore napada, specifična prevencija ovisi o ispravnoj implementaciji i testiranju:

### WannaCry-stil napadi
- **Ublažavanje**: `Set-Ghost -SMBv1` onemogućava ranjivi protokol
- **Razmatranje**: Osigurajte da nijedan zastarjeli sustav ne zahtijeva SMBv1

### RDP-bazirani ransomware
- **Ublažavanje**: `Set-Ghost -RDP` blokira pristup udaljenom radnom stolu
- **Razmatranje**: Može zahtijevati alternativne metode udaljenog pristupa

### Malware baziran na dokumentima
- **Ublažavanje**: `Set-Ghost -Macros` onemogućava izvršavanje makroa
- **Razmatranje**: Može utjecati na legitimne dokumente s omogućenim makroima

### USB-dostavljene prijetnje
- **Ublažavanje**: `Set-Ghost -USBStorage -AutoRun` ograničava USB funkcionalnost
- **Razmatranje**: Može utjecati na legitimno korištenje USB uređaja

## 🏢 Enterprise značajke

### Group Policy podrška
```powershell
# Primijenite postavke putem Group Policy registra
Set-Ghost -SMBv1 -RDP -AutoRun -GroupPolicy

# Postavke se primjenjuju domenom-široko nakon GP osvježavanja
gpupdate /force
```

### Microsoft Intune integracija
```powershell
# Stvorite Intune pravila za Ghost postavke
Set-IntuneGhost -Settings $GhostSettings -Interactive

# Pravila se automatski implementiraju na upravljane uređaje
```

### Izvještavanje o usklađenosti
```powershell
# Generirajte izvještaj sigurnosne procjene
Get-Ghost | Export-Csv -Path "SecurityAudit-$(Get-Date -Format 'yyyy-MM-dd').csv"

# Azure izvještaj sigurnosnog stanja
Get-AzureGhost | Out-File "AzureSecurityReport.txt"
```

## 📚 Najbolje prakse

### Pred-implementacija
1. **Dokumentirajte trenutno stanje**: Pokrenite `Get-Ghost` prije promjena
2. **Temeljito testirajte**: Validirajte u ne-produkcijskom okruženju
3. **Planirajte vraćanje**: Znajte kako vratiti svaku postavku
4. **Pregled dionika**: Osigurajte da poslovne jedinice odobravaju promjene

### Tijekom implementacije
1. **Postupni pristup**: Implementirajte prvo na pilot grupe
2. **Pratite utjecaj**: Pazite na korisničke pritužbe ili sistemske probleme
3. **Dokumentirajte probleme**: Zabilježite sve probleme za buduću referencu
4. **Komunicirajte promjene**: Informirajte korisnike o sigurnosnim poboljšanjima

### Post-implementacija
1. **Redovita procjena**: Periodično pokretajte `Get-Ghost` za provjeru postavki
2. **Ažurirajte dokumentaciju**: Održavajte sigurnosne konfiguracije ažurnima
3. **Pregledajte učinkovitost**: Pratite sigurnosne incidente
4. **Kontinuirano poboljšanje**: Prilagodite postavke na temelju prijetnje

## 🔧 Rješavanje problema

### Uobičajeni problemi
- **Greške dozvola**: Osigurajte povišenu PowerShell sesiju
- **Ovisnosti usluga**: Neke usluge mogu imati ovisnosti
- **Kompatibilnost aplikacija**: Testirajte s poslovnim aplikacijama
- **Mrežna povezanost**: Provjerite da udaljeni pristup još uvijek radi

### Opcije oporavka
```powershell
# Ponovno omogućite specifične usluge kada je potrebno
Set-RDP -Enable
Set-SMBv1 -Enable
Set-AutoRun -Enable
Set-Macros -Enable
```

## 👨‍💻 O autoru

**Jim Tyler** - Microsoft MVP za PowerShell
- **YouTube**: [@PowerShellEngineer](https://youtube.com/@PowerShellEngineer) (10.000+ pretplatnika)
- **Newsletter**: [PowerShell.News](https://powershell.news) - Tjedna sigurnosna inteligencija
- **Autor**: "PowerShell for Systems Engineers"
- **Iskustvo**: Desetljeća PowerShell automatizacije i Windows sigurnosti

## 📄 Licenca i odricanje

### MIT licenca
Ghost se pruža pod MIT licencom za besplatno korištenje, modificiranje i distribuciju.

### Sigurnosno odricanje
- **Nema jamstva**: Ghost se pruža "kakav jest" bez jamstva bilo koje vrste
- **Testiranje potrebno**: Uvijek testirajte u ne-produkcijskim okruženjima prvo
- **Profesionalno vodstvo**: Savjetujte se sa sigurnosnim stručnjacima za produkcijske implementacije
- **Operacijski utjecaj**: Autori nisu odgovorni za bilo kakve operacijske prekide
- **Sveobuhvatna sigurnost**: Ghost je jedna komponenta potpune sigurnosne strategije

### Podrška
- **GitHub problemi**: [Prijavite bugove ili zatražite značajke](https://github.com/jimrtyler/Ghost/issues)
- **Dokumentacija**: Koristite `Get-Help <function> -Full` za detaljnu pomoć
- **Zajednica**: PowerShell i sigurnosni forumi zajednice

---

**🔐 Ojačajte svoju sigurnosnu poziciju s Ghost - ali uvijek prvo testirajte.**

```powershell
# Počnite s procjenom, ne pretpostavkama
Get-Ghost
```

**⭐ Označite ovaj repozitorij zvjezdicom ako Ghost pomaže poboljšati vašu sigurnosnu poziciju!**