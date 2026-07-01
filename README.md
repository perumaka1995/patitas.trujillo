# Patitas Trujillo - editar estado por WhatsApp

Nueva función:
- Dentro de la ficha de cada mascota se puede cambiar el estado.
- El usuario debe ingresar el WhatsApp con el que registró el reporte.
- Puede cambiar a: Perdida, Vista, Encontrada o En adopción.
- Puede agregar una nota opcional.
- No borra el reporte ni los comentarios.

IMPORTANTE:
Para que funcione, Firestore debe permitir update en mascotas:

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
https://patitastrujillo.vercel.app/?v=14
