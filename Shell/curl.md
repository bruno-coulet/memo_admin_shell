Voici les principales options de la commande `curl` pour se connecter à une API, avec des exemples concrets pour chaque cas d'usage courant :

---

### **1. Envoyer une requête GET**
```bash
curl -X GET https://api.example.com/endpoint
```
- `-X GET` : Spécifie la méthode HTTP (GET par défaut, donc optionnelle ici).

---

### **2. Envoyer une requête POST avec des données**
```bash
curl -X POST https://api.example.com/endpoint \
     -H "Content-Type: application/json" \
     -d '{"key1":"value1", "key2":"value2"}'
```
- `-X POST` : Méthode HTTP POST.
- `-H` : Ajoute un en-tête (ici, pour spécifier le type de contenu).
- `-d` : Données envoyées dans le corps de la requête.

---

### **3. Ajouter des en-têtes (Headers)**
```bash
curl -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
     -H "Content-Type: application/json" \
     https://api.example.com/endpoint
```
- Utile pour l'authentification (ex: token Bearer) ou pour préciser le format des données.

---

### **4. Passer des paramètres dans l'URL (Query Parameters)**
```bash
curl "https://api.example.com/endpoint?param1=value1&param2=value2"
```
- Les paramètres sont ajoutés directement dans l'URL.

---

### **5. Suivre les redirections**
```bash
curl -L https://api.example.com/endpoint
```
- `-L` : Suit les redirections HTTP (3xx).

---

### **6. Ignorer la validation du certificat SSL (pour tests uniquement)**
```bash
curl -k https://api.example.com/endpoint
```
- `-k` : Ignore les erreurs de certificat SSL (à utiliser avec prudence).

---

### **7. Sauvegarder la réponse dans un fichier**
```bash
curl -o response.json https://api.example.com/endpoint
```
- `-o` : Redirige la réponse vers un fichier.

---

### **8. Afficher uniquement les en-têtes de la réponse**
```bash
curl -I https://api.example.com/endpoint
```
- `-I` : Récupère uniquement les en-têtes HTTP.

---

### **9. Envoyer des données binaires (upload de fichier)**
```bash
curl -X POST https://api.example.com/upload \
     -H "Content-Type: multipart/form-data" \
     -F "file=@/chemin/vers/fichier.pdf"
```
- `-F` : Pour envoyer un fichier en multipart/form-data.

---

### **10. Utiliser l'authentification basique**
```bash
curl -u username:password https://api.example.com/endpoint
```
- `-u` : Pour l'authentification HTTP Basic.

---

### **11. Afficher des informations détaillées sur la requête/réponse**
```bash
curl -v https://api.example.com/endpoint
```
- `-v` : Mode verbeux (débogage).

---

### **12. Limiter la vitesse de transfert**
```bash
curl --limit-rate 100K https://api.example.com/endpoint
```
- Utile pour éviter de saturer la bande passante.

---

### **Exemple complet avec authentification et données JSON**
```bash
curl -X POST https://api.example.com/users \
     -H "Authorization: Bearer YOUR_TOKEN" \
     -H "Content-Type: application/json" \
     -d '{"name":"John Doe", "email":"john@example.com"}'
```

---

### **Astuce**
Pour tester une API rapidement, tu peux aussi utiliser des outils comme [Postman](https://www.postman.com/) ou [Insomnia](https://insomnia.rest/), mais `curl` reste indispensable pour l'automatisation ou les scripts.

Besoin d’un exemple plus spécifique ou d’aide pour une API en particulier ?
