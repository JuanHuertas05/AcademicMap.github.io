# Deploy en GitHub Pages con perfiles de usuario

Este proyecto es estático y puede subirse a GitHub Pages como `index.html`.
Para perfiles de usuario y sincronización entre dispositivos usa Firebase Authentication + Firestore.

## 1. Crear proyecto Firebase
1. Entra a Firebase Console.
2. Crea un proyecto.
3. Agrega una Web App.
4. Copia la configuración `firebaseConfig`.
5. En `index.html`, busca `FIREBASE_CONFIG` y reemplaza los valores `PEGAR_*`.

## 2. Activar login
Firebase Console > Authentication > Sign-in method > Email/Password > Enable.

## 3. Crear Firestore
Firebase Console > Firestore Database > Create database.

## 4. Reglas de seguridad
Copia el contenido de `firestore.rules` en Firestore Rules y publica.

## 5. Crear administrador
1. Abre la página publicada.
2. Crea tu perfil con correo y contraseña.
3. En Firebase Console > Authentication, copia tu `UID`.
4. En Firestore crea el documento:

`admins/TU_UID`

Puede estar vacío, por ejemplo:

```json
{ "role": "admin" }
```

Ese usuario podrá publicar cambios globales.

## 6. Modelo de datos
- `users/{uid}`: avance privado de cada usuario: materias cursadas, horario, planificador y ruta por semestre.
- `global/appState`: pensum, prerrequisitos, horarios y homologaciones. Solo admin puede escribir.
- `admins/{uid}`: lista de administradores. Solo se crea manualmente desde Firebase Console.

## 7. Subir a GitHub Pages
1. Crea un repositorio.
2. Sube `index.html` y `firestore.rules`.
3. GitHub > Settings > Pages.
4. Source: Deploy from branch.
5. Branch: `main`, folder `/root`.
6. Abre la URL generada.
