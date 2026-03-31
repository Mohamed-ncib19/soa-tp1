# TP1 : Introduction à SOA & SOAP
**A.U. : 2025/2026**  
**Matière : SoA et Microservices**  
**Classe : 4Info**  
**Enseignant : Dr. Salah Gontara**

---

## Objectifs 
— Comprendre l’idée SOA : service, contrat, client, interopérabilité.   
— Comprendre la structure d’un message SOAP : Envelope, Header, Body.  
— Lire un WSDL : definitions, types, message, portType, binding, service.  
— Tester une requête SOAP via Postman et interpréter la réponse et un SOAP Fault. 

---

## Partie A — SOA & lecture du WSDL (le contrat)

### A2. Exploration du WSDL 
WSDL URL : [https://apps.learnwebservices.com/services/hello?WSDL](https://apps.learnwebservices.com/services/hello?WSDL)

**Rôle des éléments vus :**
- `<wsdl:definitions>` : Racine du contrat, définit les namespaces et l'organisation globale.
- `<wsdl:types>` : Contient le schéma XSD décrivant les structures de données (types complexes).
- `<wsdl:message>` : Définit les données de l'opération (en entrée et sortie) en se référant aux types XSD.
- `<wsdl:portType>` : Interface abstraite regroupant les opérations (équivalent d'une classe/interface).
- `<wsdl:binding>` : Détails techniques (protocole de transport, style de codage).
- `<wsdl:service>` : Point d'accès final (endpoint) où le service est hébergé.

### A3. Questions
1. **Où le WSDL donne-t-il l’URL du service ?**  
   L'URL se trouve dans l'élément `<ns1:address location="...">` à l'intérieur de `<wsdl:port>` sous `<wsdl:service>`.

2. **Où sont définis les champs Name (entrée) et Message (sortie) ?**  
   Ils sont définis dans la section `<wsdl:types>` à l'aide d'un schéma XML (XSD).

3. **Quelle différence entre portType et binding ?**  
   `portType` est une définition abstraite (quoi faire), alors que `binding` est une définition concrète (comment le faire en termes de protocole et de format).

4. **Quel est le nom de l’opération exposée par ce service ?**  
   L'opération s'appelle `SayHello`.

---

## Partie B — SOAP Envelope & appel avec Postman

### B5. Questions
1. **Dans la réponse, où se trouve le payload métier ?**  
   Le payload métier se trouve à l'intérieur de la balise `<soap:Body>`.

2. **Quel tag contient le message final ?**  
   C'est le tag `<Message>`.

3. **Indiquer ce qui relève de la structure SOAP vs des données métier.**  
   - **Structure SOAP** : `<soap:Envelope>`, `<soap:Header>`, `<soap:Body>`.
   - **Données métier** : `<HelloResponse>`, `<Message>`.

---

## Partie C — Provoquer et analyser un SOAP Fault

### C3. Questions
1. **Relever faultcode et dire s’il s’agit d’une erreur côté client ou serveur.**  
   Le `faultcode` relevé est généralement `soap:Client` (ou `Client`). Cela indique que la requête envoyée par le client est incorrecte (mal formée).

2. **Relever faultstring et expliquer l’origine probable de l’erreur.**  
   Le `faultstring` contient un message d'erreur expliquant le problème de parsing (ex: "Unexpected element" ou "Unmarshalling Error"). L'origine est une erreur de syntaxe dans l'XML de la requête.

3. **Où se trouve le Fault dans la structure SOAP (Header ou Body) ?**  
   L'élément `<soap:Fault>` se trouve toujours dans le `<soap:Body>`.

---

### GitHub Repository
[https://github.com/Mohamed-ncib19/soa-tp1](https://github.com/Mohamed-ncib19/soa-tp1)
