# PagePal - AI-Powered Voice Book Reader

**PagePal** is an innovative web application that transforms the way you consume books. By combining AI voice synthesis with intelligent text segmentation, PagePal allows users to listen to their favorite books with natural-sounding voice narration powered by AI.

🔗 **Live Demo:** [https://pagepal-nine.vercel.app](https://pagepal-nine.vercel.app)

---

## 🎯 Project Overview

PagePal is designed to make reading more accessible and convenient by enabling users to:
- **Upload PDF books** with automatic cover image recognition
- **Listen to books** using high-quality AI voice synthesis
- **Track reading progress** with segment-based navigation
- **Manage multiple books** with an organized library interface
- **Choose voice personalities** for different listening experiences
- **Monitor usage** based on their subscription plan

The application leverages modern web technologies and AI services to create a seamless audiobook experience directly in your browser.

---

## 🚀 Key Features

### 📚 Book Management
- **PDF Upload & Processing**: Upload PDF files with intelligent segmentation into manageable chunks
- **Metadata Extraction**: Automatic extraction of book title, author, and generation of book slugs
- **Cover Image Support**: Store and display cover images for each book
- **Library Dashboard**: Browse and manage all uploaded books in one place

### 🎙️ Voice Synthesis
- **AI Voice Integration**: Powered by Vapi AI for natural-sounding voice narration
- **Multiple Voice Options**: Choose from various voice personas to match your preference
- **Real-time Audio Playback**: Stream audio segments seamlessly
- **Session Management**: Track voice reading sessions with duration and billing information

### 📊 Subscription & Usage Limits
- **Tiered Plans**: Different subscription levels with varying audio session limits
- **Usage Tracking**: Monitor monthly session counts and maximum duration per session
- **Billing Period Management**: Automatic reset of monthly session limits

### 🔐 User Authentication
- **Secure Auth**: Powered by Clerk for robust user authentication
- **User Isolation**: Each user's books and sessions are completely isolated
- **Session Tracking**: Link all user activities to their unique Clerk ID

---

## 🏗️ Architecture & Technology Stack

### Frontend
- **Framework**: [Next.js 16.2.4](https://nextjs.org/) - React meta-framework with App Router
- **Language**: [TypeScript](https://www.typescriptlang.org/) - Type-safe JavaScript
- **UI Components**: 
  - [shadcn/ui](https://ui.shadcn.com/) - High-quality component library
  - [Radix UI](https://www.radix-ui.com/) - Unstyled, accessible primitives
  - [Lucide React](https://lucide.dev/) - Beautiful icon library
- **Styling**: 
  - [Tailwind CSS 4](https://tailwindcss.com/) - Utility-first CSS framework
  - [Tailwind Merge](https://github.com/dcastil-dev/tailwind-merge) - Merge Tailwind classes
- **Forms**: 
  - [React Hook Form](https://react-hook-form.com/) - Performant form library
  - [Zod](https://zod.dev/) - TypeScript-first schema validation

### Backend
- **Database**: 
  - [MongoDB](https://www.mongodb.com/) - NoSQL document database
  - [Mongoose](https://mongoosejs.com/) - MongoDB object modeling
- **File Storage**: [Vercel Blob](https://vercel.com/docs/storage/vercel-blob) - Cloud file storage
- **PDF Processing**: [pdfjs-dist](https://mozilla.github.io/pdf.js/) - Client-side PDF parsing and text extraction
- **Voice Synthesis**: [Vapi AI](https://vapi.ai/) - AI voice API integration

### Utilities
- **Notifications**: [Sonner](https://sonner.emilkowal.ski/) - Toast notifications
- **Styling Utilities**: [clsx](https://github.com/lukeed/clsx), [Class Variance Authority](https://cva.style/) - Class name utilities
- **Environment Management**: [Zod](https://zod.dev/) - Schema validation for config

### Development Tools
- **Linting**: [ESLint 9](https://eslint.org/) with Next.js config
- **Code Quality**: TypeScript strict mode enabled
- **Build Optimization**: Next.js optimizations for performance

---

## 📁 Project Structure

```
pagepal/
├── app/                    # Next.js App Router pages and API routes
├── components/             # Reusable React components
├── hooks/                  # Custom React hooks
├── lib/                    # Utility functions and helpers
├── database/               # MongoDB Mongoose models and schemas
├── public/                 # Static assets (images, fonts, etc.)
├── types.d.ts              # TypeScript type definitions
├── package.json            # Project dependencies and scripts
├── tsconfig.json           # TypeScript configuration
├── next.config.ts          # Next.js configuration
├── components.json         # shadcn/ui component registry
├── tailwind.config.js      # Tailwind CSS configuration
├── postcss.config.mjs      # PostCSS configuration
└── AGENTS.md               # AI agent guidelines for development
```

---

## 🗄️ Data Models

### IBook
Represents a book in the library:
- Stores PDF file references and metadata
- Tracks total segments for pagination
- Links to user via `clerkId`
- Includes timestamps for audit trail

### IBookSegment
Represents a chunk of book content:
- Stores extracted text from PDF
- Tracks word count and page numbers
- Associated with parent book via `bookId`

### IVoiceSession
Tracks user voice/audio sessions:
- Records start and end times
- Calculates duration for billing
- Links to billing period for usage tracking

---

## 🛠️ Getting Started

### Prerequisites
- Node.js 18+ and npm/yarn
- MongoDB instance (local or cloud)
- Clerk account for authentication
- Vapi AI API key for voice synthesis
- Vercel Blob account for file storage

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/BahrouniAyoub/pagepal.git
   cd pagepal
   ```

2. **Install dependencies:**
   ```bash
   npm install
   # or
   yarn install
   # or
   pnpm install
   ```

3. **Set up environment variables:**
   Create a `.env.local` file in the root directory:
   ```env
   # Clerk Authentication
   NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
   CLERK_SECRET_KEY=your_clerk_secret_key

   # MongoDB
   MONGODB_URI=your_mongodb_connection_string

   # Vapi AI
   VAPI_PUBLIC_API_KEY=your_vapi_public_key
   VAPI_SECRET_KEY=your_vapi_secret_key

   # Vercel Blob
   BLOB_READ_WRITE_TOKEN=your_vercel_blob_token
   ```

4. **Run the development server:**
   ```bash
   npm run dev
   # or
   yarn dev
   # or
   pnpm dev
   ```

5. **Open in browser:**
   Navigate to [http://localhost:3000](http://localhost:3000)

---

## 📜 Available Scripts

- **`npm run dev`** - Start development server with hot reload
- **`npm run build`** - Build application for production
- **`npm run start`** - Start production server
- **`npm run lint`** - Run ESLint to check code quality

---

## 🎯 Use Cases

- **Accessibility**: Make reading accessible to visually impaired users
- **Multitasking**: Listen to books while commuting, exercising, or doing chores
- **Language Learning**: Use AI voices to practice language pronunciation
- **Accessibility Features**: Adjustable voice speeds and natural language narration
- **Book Club Discussion**: Listen to the same books with consistent narration

---

## 🔮 Future Enhancements

- [ ] Multiple language support
- [ ] Book highlighting and note-taking features
- [ ] Social sharing and collaborative reading
- [ ] Advanced audio controls (pitch, speed, effects)
- [ ] Offline listening capability
- [ ] Reading analytics and progress tracking
- [ ] Integration with popular book platforms (Goodreads, etc.)

---

## 📝 License

This project is open source and available under the MIT License.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

## 📧 Support

For issues, questions, or suggestions, please open an issue on the [GitHub repository](https://github.com/BahrouniAyoub/pagepal/issues).

---

## 🙏 Acknowledgments

- [Next.js](https://nextjs.org/) - The React framework
- [Clerk](https://clerk.com/) - Authentication platform
- [Vapi AI](https://vapi.ai/) - Voice synthesis API
- [Vercel](https://vercel.com/) - Hosting and blob storage
- [shadcn/ui](https://ui.shadcn.com/) - Component library
- All the amazing open-source libraries that make this project possible
