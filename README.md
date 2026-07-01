# Patitas Trujillo - cambiar estado visible

Corrección:
- Ahora la opción para cambiar estado aparece antes de Comentarios y avistamientos.
- El dueño debe ingresar el WhatsApp registrado.
- Puede marcar como Encontrada, Vista, Perdida o En adopción.
- Puede dejar una nota opcional.
- No borra el reporte ni los comentarios.

REGLAS FIREBASE NECESARIAS:

rules_version = '2';

service cloud.firestore {
  match /databases/{database}/documents {

    match /mascotas/{mascotaId} {
      allow read: if true;
      allow create: if true;
      allow update: if true;
      allow delete: if false;

      match /comentarios/{comentarioId} {
        allow read: if true;
        allow create: if true;
        allow update, delete: if false;
      }
    }

    match /estadisticas/{docId} {
      allow read: if true;
      allow create, update: if true;
      allow delete: if false;
    }
  }
}

Sube todos los archivos a GitHub y abre:
https://patitastrujillo.vercel.app/?v=15
