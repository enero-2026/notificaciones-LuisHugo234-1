# Historial de Asistencia con IA (Copilot / Gemini)

## Problema 1: Error de dependencias al instalar
**Prompt del alumno:**
Tengo el siguiente error al ejecutar el programa instalándolo con las dependencias que me dijo la profe: `CommandError: "react-native-web" is added as a dependency in your project's package.json but it doesn't seem to be installed. Run "npm install", or the equivalent for your package manager, and try again.` Al usar `npm install` me da el error `ERESOLVE unable to resolve dependency tree`.

**Solución de la IA:**
El error `ERESOLVE` ocurre por un conflicto de versiones entre `react@19.1.0` y las versiones que piden `react-dom` y `react-native-web`. La solución fue forzar la instalación ignorando las advertencias estrictas de versiones ejecutando el comando:
`npm install --legacy-peer-deps`
Después de eso, se pudo iniciar la aplicación correctamente con `npx expo start`.

---

## Problema 2: Estructurar el código de Notificaciones y AsyncStorage
**Prompt del alumno:**
[Se proporcionaron los fragmentos de código de las instrucciones para expo-notifications y async-storage] Al utilizar lo del principio de las notificaciones me da error en una línea de código, ¿puedes apoyarme solucionándolo y conectando el código de notificación con el de AsyncStorage para el ejercicio final?

**Solución de la IA:**
El error ocurría porque los fragmentos de código estaban sueltos y no estaban envueltos en la estructura principal del componente de React Native. Se realizaron los siguientes ajustes:
1. Se envolvió todo dentro de `export default function App() { ... }` y un bloque `return (...)` para la interfaz.
2. Se agregaron los imports faltantes de `useState` y `useEffect`.
3. Se agregó `Notifications.setNotificationHandler` para asegurar que las notificaciones se muestren incluso con la app en primer plano.
4. Se corrigió la sintaxis de `Notifications.scheduleNotificationAsync`.
5. Para resolver el ejercicio final, se inyectó la variable de estado dentro del cuerpo de la notificación usando template strings: `body: \`Esta es tu primera notificación. El contador va en: ${contador}\``.
