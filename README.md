# patitas.trujillo - re-subir foto

Nueva función:
- Dentro de la ficha de cada mascota aparece "Subir / cambiar foto".
- Permite cargar nuevamente una imagen si la primera no subió bien.
- Solo actualiza la fotoURL del reporte en Firestore.
- No borra el reporte ni los comentarios.

IMPORTANTE:
Cambia las reglas de Firestore para permitir update en mascotas:

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

Después abre:
https://patitastrujillo.vercel.app/?v=10
