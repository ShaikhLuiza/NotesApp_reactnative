# 📝 React Native Notes App

A simple and professional **Notes CRUD application** built with **React Native CLI (without Expo)** and **AsyncStorage**.

The app allows users to create, view, edit, delete, and search notes. All notes are stored locally on the device, so no backend or database server is required.

---

## ✨ Features

* 📝 Create notes
* 👀 View saved notes
* ✏️ Edit existing notes
* 🗑️ Delete notes
* 🔍 Search notes
* 💾 Local data persistence with AsyncStorage
* 📱 React Native CLI — no Expo
* 🎨 Professional light-theme UI
* 🖼️ Online background image
* 📦 TypeScript support
* ⚡ Fast and lightweight

---

## 📱 Screenshots

 <p align="center"> <img src="https://github.com/user-attachments/assets/23ce225d-35fc-4252-afbf-6ba2df1da30f" width="250" /> <img src="https://github.com/user-attachments/assets/09b95d4c-95fe-4fa8-8b63-c81ead6bee4e" width="250" /> <img src="https://github.com/user-attachments/assets/1b4129d6-7f77-43b5-a83c-d68b4b59bd62" width="250" />  <img src="https://github.com/user-attachments/assets/3d53b03c-ce7d-4caa-be42-e09f0dfa8314" width="250" /></p>

<p align="center"> 
  <img src="https://github.com/user-attachments/assets/9753bf5a-e877-43b5-819a-3f60a7d7f761" width="250" /> <img src="https://github.com/user-attachments/assets/06c593a8-094a-4e46-94ca-88154bccd5cb" width="250" />
</p>






---

## 🛠️ Technologies Used

| Technology   | Purpose                        |
| ------------ | ------------------------------ |
| React Native | Mobile application framework   |
| TypeScript   | Type-safe JavaScript           |
| AsyncStorage | Local data storage             |
| React Hooks  | State and lifecycle management |
| FlatList     | Efficient note list rendering  |

---

## 📂 Project Structure

```text
NotesApp/
│
├── android/
├── ios/
├── node_modules/
│
├── App.tsx
├── package.json
├── tsconfig.json
├── babel.config.js
├── metro.config.js
├── .gitignore
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/notes-app.git
```

Go inside the project:

```bash
cd notes-app
```

---

### 2. Install dependencies

```bash
npm install
```

---

### 3. Install AsyncStorage

```bash
npm install @react-native-async-storage/async-storage
```

---

### 4. Start Metro

```bash
npm start
```

---

### 5. Run on Android

Open another terminal:

```bash
npx react-native run-android
```

Make sure an Android emulator is running or a physical Android device is connected with USB debugging enabled.

---

## 💾 How Local Storage Works

This project uses **AsyncStorage** to store notes locally on the device.

The storage key is:

```tsx
const STORAGE_KEY = '@professional_notes';
```

When notes are saved, they are converted into JSON:

```tsx
await AsyncStorage.setItem(
  STORAGE_KEY,
  JSON.stringify(updatedNotes)
);
```

When the application starts, the stored data is retrieved:

```tsx
const savedNotes =
  await AsyncStorage.getItem(STORAGE_KEY);
```

Then it is converted back into a JavaScript array:

```tsx
JSON.parse(savedNotes);
```

The basic flow is:

```text
User creates note
       ↓
JavaScript object
       ↓
JSON.stringify()
       ↓
AsyncStorage
       ↓
Phone's private app storage
```

---

## 🔄 CRUD Operations

This application demonstrates all four basic CRUD operations.

### Create

Users can create a new note by entering:

* Title
* Description

```tsx
const newNote: Note = {
  id: Date.now().toString(),
  title: title.trim(),
  description: description.trim(),
};
```

### Read

Notes are loaded from AsyncStorage when the application starts:

```tsx
useEffect(() => {
  loadNotes();
}, []);
```

### Update

Users can select a note and modify its title or description.

```tsx
const updatedNotes = notes.map(note =>
  note.id === editingId
    ? {
        ...note,
        title: title.trim(),
        description: description.trim(),
      }
    : note,
);
```

### Delete

A note can be removed from the list:

```tsx
const updatedNotes = notes.filter(
  note => note.id !== id,
);
```

---

## 🔎 Search

The application includes a search feature that searches through both the note title and description.

```tsx
const filteredNotes = notes.filter(note =>
  `${note.title} ${note.description}`
    .toLowerCase()
    .includes(search.toLowerCase()),
);
```

---

## 🎨 UI Design

The application uses a clean, modern light interface.

### Design Elements

* Soft background image
* White cards
* Rounded corners
* Subtle shadows
* Purple primary action color
* Minimal typography
* Clean input fields
* Responsive layout
* Mobile-friendly spacing

---

## 🖼️ Background Image

The application uses an online Unsplash image as the background.

For production applications, it is recommended to download the image and include it as a local asset instead of relying on an external URL.

For example:

```text
assets/
└── images/
    └── notes-background.jpg
```

Then:

```tsx
<ImageBackground
  source={require('./assets/images/notes-background.jpg')}
  style={styles.background}
>
```

---

## 📦 Dependencies

Main dependency:

```bash
npm install @react-native-async-storage/async-storage
```

The project otherwise uses React Native's built-in components such as:

* `FlatList`
* `TextInput`
* `Pressable`
* `ImageBackground`
* `KeyboardAvoidingView`
* `SafeAreaView`

---

## 🔐 Data & Privacy

This application does **not use a backend**.

Notes are stored locally using AsyncStorage.

```text
Phone
  │
  └── Your Notes App
        │
        └── AsyncStorage
              │
              └── Local app storage
```

Your notes are not automatically uploaded to a server.

> **Note:** Uninstalling the application will normally remove its private local storage, including the stored notes.

---

## 🧪 Future Improvements

Possible improvements for future versions:

* [ ] Add note categories
* [ ] Add favorite notes
* [ ] Add note colors
* [ ] Add dark mode
* [ ] Add date and time
* [ ] Add note details screen
* [ ] Add React Navigation
* [ ] Add animations
* [ ] Add authentication
* [ ] Replace AsyncStorage with SQLite
* [ ] Add cloud synchronization
* [ ] Add export/import notes
* [ ] Generate Android APK

---

## 📚 What I Learned

This project is useful for learning:

* React Native fundamentals
* TypeScript
* Functional components
* `useState`
* `useEffect`
* `useMemo`
* CRUD operations
* Local storage
* AsyncStorage
* JSON serialization
* `FlatList`
* Form handling
* Search/filtering
* Android application development
* Professional mobile UI design
