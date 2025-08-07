
# 🖼️ Image Generation App – alx-project-0x08

This project is a continuation of the ALX Front-End curriculum. It builds on the `alx-project-0x07` setup by introducing basic **React state management** to enhance interactivity and user experience.


## 📌 Objective

> **Modify the application to track basic states**, making the image generation app more dynamic and interactive. The application was duplicated from `alx-project-0x07` and updated to introduce local state with `useState`.


## 📁 Project Structure

```bash

alx-project-0x08/
├── components/
│   └── layouts/
│       ├── Footer.tsx
│       ├── Header.tsx
│       ├── Layout.tsx
│   └── common/
│       └── ImageCard.tsx     ← New component added
├── interfaces/
│   └── index.ts              ← Updated interface definitions
├── pages/
│   ├── \_app.tsx
│   └── index.tsx             ← Main logic updated with state
├── README.md

````


## 🧠 Features Implemented

### ✅ State Management with `useState`
The app now keeps track of:
- `prompt`: User's input prompt for image generation.
- `imageUrl`: The currently displayed/generated image.
- `generatedImages`: A list to hold all previously generated images (structure in place).
- `isLoading`: Loading state for UX improvement during image generation.

### ✅ Interface Updates
The `interfaces/index.ts` file now contains:

```ts
import { ReactNode } from "react";

export interface ReactComponentProps {
  children: ReactNode;
}

export interface GeneratedImageProps {
  imageUrl: string;
  prompt: string;
  width?: string;
  height?: string;
  action: (imagePath: string) => void;
}

export type ImageProps = Pick<GeneratedImageProps, "imageUrl" | "prompt">;

````


### ✅ New Component: `ImageCard`

Displays a single image along with the prompt. Clickable and reusable.

```tsx
const ImageCard: React.FC<GeneratedImageProps> = ({ imageUrl, prompt, width, action }) => {
  return (
    <div onClick={() => action(imageUrl)} className="mt-6 border hover:cursor-pointer">
      <img src={imageUrl} alt={prompt} className={`w-full max-w-md rounded-lg shadow-lg`} />
      <h2 className={`${width ? 'text-sm' : 'text-xl'} font-semibold mt-2`}>Your Prompt:</h2>
      <p className={`${width ? 'text-xs' : 'text-lg'} text-gray-700 mb-4`}>{prompt}</p>
    </div>
  );
}
```

### ✅ Updated Home Page (`index.tsx`)

* Integrates all state management features.
* Handles user input.
* Prepares for async image generation.
* Utilizes `ImageCard` component for displaying results.


## 🚀 How to Run Locally

1. **Clone the repo:**

```bash
git clone https://github.com/AnalystYuchels/alx-project-0x08.git
cd alx-project-0x08
```

2. **Install dependencies:**

```bash
npm install
```

3. **Start the development server:**

```bash
npm run dev
```

4. **Open in browser:**
   Visit `http://localhost:3000` to view the app.
