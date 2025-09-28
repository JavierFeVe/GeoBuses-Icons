# 📦 Uso de iconos personalizados de IcoMoon en React Native

Este proyecto incluye un pack de iconos generado con **IcoMoon**. A continuación se explica cómo integrarlos en una aplicación **React Native** usando [`react-native-vector-icons`](https://github.com/oblador/react-native-vector-icons).

---

## 1️⃣ Archivos necesarios

Dentro de tu carpeta (ejemplo: `/assets/icomoon/`) deben estar al menos:

```
/assets/icomoon/
   style.css
   icomoon.ttf
   selection.json
```

---

## 2️⃣ Añadir la fuente a tu proyecto

1. Copia el archivo `icomoon.ttf` a la carpeta `assets/fonts/` de tu proyecto.  
   Ejemplo:
   ```
   /assets/fonts/icomoon.ttf
   ```

2. En la raíz del proyecto, crea o edita el archivo `react-native.config.js`:

   ```js
   module.exports = {
     assets: ['./assets/fonts'],
   };
   ```

3. Ejecuta en consola:

   ```bash
   npx react-native link
   ```

---

## 3️⃣ Crear el componente de iconos

Usaremos `createIconSetFromIcoMoon` para importar el set:

```js
// components/MyIcons.js
import { createIconSetFromIcoMoon } from 'react-native-vector-icons';
import icoMoonConfig from '../assets/icomoon/selection.json';

const MyIcons = createIconSetFromIcoMoon(
  icoMoonConfig,
  'icomoon',   // Debe coincidir con "font-family" en style.css
  'icomoon.ttf'
);

export default MyIcons;
```

---

## 4️⃣ Usar los iconos en tu app

Ahora ya puedes usar tus iconos como cualquier otro set de `react-native-vector-icons`:

```js
import MyIcons from './components/MyIcons';

export default function App() {
  return (
    <>
      <MyIcons name="coche" size={40} color="blue" />
      <MyIcons name="feria" size={50} color="red" />
    </>
  );
}
```

El valor de `name` corresponde al que se asignó en IcoMoon cuando exportaste los SVGs.

---

✅ Con esto, tienes tu **propio pack de iconos personalizado** integrado en React Native, funcionando igual que FontAwesome pero con tus propios diseños.
