# Fishing Pro Mobile — 0.2.0

Proyecto de código fuente para Android e iOS con Capacitor 7. **No incluye un APK ni un IPA ya compilados.**

## Funciones actuales
- Panel meteorológico con Open-Meteo (requiere Internet y autorización de ubicación).
- Mapa OpenStreetMap con opción de satélite Esri, selección GPS y spots privados guardados localmente.
- Diario de capturas local, exportación JSON e importación JSON.
- Fase lunar aproximada y estimación ilustrativa de actividad **no validada científicamente**.
- Accesos externos a YouTube, Spotify y búsquedas de tiendas.
- PWA con caché de la interfaz; mapas y datos meteorológicos no garantizados sin conexión.

## Generar APK Android
1. Instalar Node.js 22, Java 21 y Android Studio con Android SDK.
2. `npm ci` (si existe package-lock.json) o `npm install`.
3. `npx cap add android` (solo primera vez); `npx cap sync android`.
4. `cd android && ./gradlew assembleDebug` (Windows: `gradlew.bat assembleDebug`).
5. APK de pruebas en `android/app/build/outputs/apk/debug/app-debug.apk`.
6. Para publicar se necesita un AAB de release firmado con una clave privada estable y cuenta Google Play Console.

## Generar iOS
En macOS con Xcode y cuenta Apple Developer: `npm install`, `npx cap add ios`, `npx cap sync ios`, `npx cap open ios`. Configurar equipo de firma, identificador de app, permisos de ubicación y distribución en Xcode / TestFlight. No existe un APK instalable en iPhone.

## Actualizaciones futuras
Modificar `www/`, incrementar versión de `package.json`, ejecutar `npx cap sync` y generar una nueva compilación. Mantener siempre el mismo `appId` y las mismas claves de firma para actualizar sin perder la identidad de la aplicación. Los datos locales pueden perderse si se desinstala: exportar copia JSON antes.

## Limitaciones y pendientes para lanzamiento público
No hay cuentas, sincronización en la nube, moderación de spots, especies verificadas por zona, temperaturas de agua, predicciones de pesca contrastadas ni integración autenticada de YouTube/Spotify. Open-Meteo y proveedores de mapas requieren comprobar condiciones y licencias de uso comercial antes de distribuir públicamente. Las tiendas son enlaces externos, no compras integradas. El permiso de ubicación y la política de privacidad deben configurarse y revisarse antes de publicar. Probar en teléfonos reales y revisar accesibilidad, uso sin red, y seguridad. La CI Android genera **APK debug**, no una versión lista para Google Play.
