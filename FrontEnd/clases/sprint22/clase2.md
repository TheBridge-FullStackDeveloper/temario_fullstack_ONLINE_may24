# Introducción a Redux y Redux Toolkit en React

Redux es una biblioteca de gestión de estado predecible para aplicaciones JavaScript, especialmente útil en aplicaciones de React. Redux Toolkit, por otro lado, es un conjunto de herramientas que simplifican el uso de Redux al proporcionar patrones de código comunes y facilitar la configuración de un store de Redux.

## ¿Qué es Redux?

Redux es una biblioteca de gestión de estado que sigue el patrón de arquitectura Flux. Su objetivo principal es mantener el estado de la aplicación en un único objeto llamado "store" y permitir que los componentes accedan y actualicen este estado de manera predecible y coherente.

En el contexto de una aplicación React, Redux se utiliza para gestionar el estado global de la aplicación, como el estado de usuario, datos recuperados del servidor, preferencias de usuario, etc.

## Principios Básicos de Redux

1. **Store**: Un objeto que contiene el estado global de la aplicación.
2. **Acciones (Actions)**: Objetos que representan eventos que pueden modificar el estado.
3. **Reducers**: Funciones puras que especifican cómo el estado de la aplicación cambia en respuesta a las acciones.

## Redux Toolkit

Redux Toolkit es una librería oficial de Redux que proporciona un conjunto de herramientas y utilidades para facilitar el uso de Redux en aplicaciones React. Algunas características clave de Redux Toolkit son:

1. **createSlice**: Una función que permite definir acciones y reducers en un solo lugar de forma más concisa.
2. **createAction**: Una función que crea acciones Redux sin necesidad de escribir código repetitivo.
3. **configureStore**: Una función que combina la configuración del store Redux con características adicionales como el middleware Redux Thunk para manejar acciones asíncronas.
4. **createAsyncThunk**: Una función que simplifica la gestión de acciones asíncronas en Redux.

## Ejemplo de Uso de Redux Toolkit

Veamos un ejemplo simple de cómo usar Redux Toolkit en una aplicación React para gestionar un contador.

```jsx
// store.js
import { configureStore, createSlice } from "@reduxjs/toolkit";

const contadorSlice = createSlice({
  name: "contador",
  initialState: {
    valor: 0,
  },
  reducers: {
    incrementar: (state) => {
      state.valor += 1;
    },
    decrementar: (state) => {
      state.valor -= 1;
    },
  },
});

export const { incrementar, decrementar } = contadorSlice.actions;

export default configureStore({
  reducer: contadorSlice.reducer,
});
```

```jsx
// App.js
import React from "react";
import { useSelector, useDispatch } from "react-redux";
import { incrementar, decrementar } from "./store";

function App() {
  const valorContador = useSelector((state) => state.valor);
  const dispatch = useDispatch();

  return (
    <div>
      <h1>Contador: {valorContador}</h1>
      <button onClick={() => dispatch(incrementar())}>Incrementar</button>
      <button onClick={() => dispatch(decrementar())}>Decrementar</button>
    </div>
  );
}

export default App;
```

En este ejemplo, hemos definido un slice de estado para el contador utilizando `createSlice` de Redux Toolkit. Luego, configuramos el store Redux utilizando `configureStore` y definimos acciones (`incrementar` y `decrementar`) que se utilizan en el componente `App` para gestionar el estado del contador.

Redux Toolkit simplifica enormemente la configuración de Redux al proporcionar patrones de código comunes y herramientas que mejoran la productividad del desarrollador y la claridad del código.
