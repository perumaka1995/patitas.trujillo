# Patitas Trujillo - botón visible para cambiar estado

Corrección:
- Ahora aparece un botón visible debajo de Contactar:
  "✅ Cambiar estado / Ya fue encontrada"
- Al hacer click se abre una ventana para ingresar el WhatsApp registrado.
- Puede cambiar a Perdida, Vista, Encontrada o En adopción.
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
https://patitastrujillo.vercel.app/?v=16
