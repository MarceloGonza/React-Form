# CustomForm - React Hook Form + Zod + Custom Input

Este proyecto implementa un formulario personalizado en React utilizando **React Hook Form** para el manejo de formularios y **Zod** como esquema de validación. Los inputs están encapsulados en un componente reutilizable llamado `InputForm`.

## 📦 Tecnologías utilizadas

- [React Hook Form](https://react-hook-form.com/)
- [Zod](https://zod.dev/)
- [@hookform/resolvers](https://react-hook-form.com/docs/useform/#resolver)
- TypeScript

## 🧩 Estructura del formulario

El formulario incluye los siguientes campos:

- **Name**
- **Email**
- **Password**
- **Confirm Password**

Cada campo utiliza el componente `InputForm` que recibe las siguientes props:

- `name`: nombre del campo
- `control`: controlador de React Hook Form
- `label`: etiqueta del input
- `type`: tipo de input (`text`, `email`, `password`, etc.)
- `error`: error de validación proporcionado por React Hook Form

## 🧪 Validación

La validación del formulario se realiza utilizando **Zod** a través del `zodResolver`. El esquema se define en el archivo `models.ts` y se importa al componente principal.

```ts
import { z } from "zod";

export const schema = z.object({
  name: z.string().min(1, "Name is required"),
  email: z.string().email("Invalid email"),
  password: z.string().min(6, "Password must be at least 6 characters"),
  confirmPassword: z.string().min(6, "Confirm your password"),
}).refine((data) => data.password === data.confirmPassword, {
  message: "Passwords do not match",
  path: ["confirmPassword"],
});

export type FormValues = z.infer<typeof schema>;


🚀Cómo usarlo

Instala las dependencias necesarias:

npm install react-hook-form zod @hookform/resolvers
```
