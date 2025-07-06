# QRPlate

> A sleek and modern QR code menu system for restaurants, cafés, and food services.

QRPlate is a fully responsive web application that enables restaurants to share digital menus via QR codes. Built with modern web technologies like React, Next.js, TailwindCSS, and Supabase, it delivers a fast, interactive, and mobile-friendly experience for diners.

---

## 👤 Author

**Albert0130**  
- [GitHub](https://github.com/albert0130)

---

## 🎯 Features

- Dynamic QR code generation for digital menus
- Responsive design optimized for mobile users
- Supabase backend with real-time database
- Menu builder using JSON collections and items
- Easy deployment with environment variables

---

## 🚀 Tech Stack

- [Next.js](https://nextjs.org)
- [React](https://reactjs.org)
- [TypeScript](https://www.typescriptlang.org)
- [Tailwind CSS](https://tailwindcss.com)
- [Supabase](https://supabase.com)
- [Radix UI](https://www.radix-ui.com)
- [@shortcm/qr-image](https://github.com/Short-io/qr-image)
- [React Hot Toast](https://react-hot-toast.com)

---

## 📸 Screenshots

![screenshot](https://user-images.githubusercontent.com/31930091/225359728-0e182455-de41-4131-883d-6b92bd0ac87d.png)
![menu-ui](https://user-images.githubusercontent.com/31930091/225359301-6e3965a0-4891-437a-9a9e-2dd1ffc5604d.png)
![restaurant-view](https://user-images.githubusercontent.com/31930091/225359169-4c26334b-5bcc-46cb-bc60-b4b465609480.png)

---

## ⚙️ Getting Started

### 1. Install Dependencies

```bash
npm install
```

### 2. Run the App

```bash
npm run dev
```

---

## 🌱 Environment Variables

Create a `.env.local` file in your root directory:

```env
NEXT_PUBLIC_SUPABASE_URL=your-supabase-url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key
```

---

## 🛠 Supabase SQL Setup

### Function: `generate_uid`

```sql
CREATE OR REPLACE FUNCTION generate_uid(size INT) RETURNS TEXT AS $$
DECLARE
  characters TEXT := 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789';
  bytes BYTEA := gen_random_bytes(size);
  l INT := length(characters);
  i INT := 0;
  output TEXT := '';
BEGIN
  WHILE i < size LOOP
    output := output || substr(characters, get_byte(bytes, i) % l + 1, 1);
    i := i + 1;
  END LOOP;
  RETURN output;
END;
$$ LANGUAGE plpgsql VOLATILE;
```

### Tables: `shops` and `menus`

*(Use your SQL editor in Supabase to run these full schema definitions with policies and triggers. They are included in `docs/setup.sql` if applicable.)*

---

## 📦 Contributing

1. Fork this repo
2. Create a branch: `git checkout -b feature/my-feature`
3. Commit: `git commit -m "Add my feature"`
4. Push: `git push origin feature/my-feature`
5. Open a pull request

---

## 💡 How It Works

Diners scan the QR code using their phone camera. They’re instantly taken to a fast, responsive digital menu where they can browse items — no downloads or logins required.

---

## 📄 License

This project is licensed under the MIT License.

---

## ✨ Final Thoughts

Whether you're launching a digital-first restaurant or upgrading from paper menus, **QRPlate** provides a clean, scalable solution for showcasing your menu through the power of QR technology.
