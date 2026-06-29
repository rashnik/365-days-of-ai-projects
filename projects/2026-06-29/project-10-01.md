Here's a unique final-year B.Tech CSE project, combining Frontend and AI, with all the specified requirements:

---

# 1. Project Name
**SynapseForge: AI-Powered Knowledge Weaver**

# 2. Problem Statement
In the digital age, individuals, researchers, and students are constantly inundated with information from diverse sources—documents, notes, web articles, and more. This wealth of data often remains siloed, unstructured, and disparate, making it challenging to synthesize, cross-reference, and extract meaningful insights. Traditional note-taking tools are largely passive, requiring significant manual effort for organization, connection-making, and retrieval, leading to missed insights and inefficient knowledge management. The core problem is the lack of an intelligent system that can automatically transform raw, unstructured information into an interconnected, queryable, and insightful personal knowledge base, thereby enhancing understanding and accelerating learning or decision-making.

# 3. Features

### Core Functionality:
1.  **Multi-format Document Ingestion:**
    *   Upload various document types: PDF, TXT, DOCX, Markdown.
    *   Paste raw text or provide web article URLs for automated scraping.
2.  **Automated Key Concept & Entity Extraction:**
    *   AI identifies and extracts core concepts, named entities (people, organizations, locations), and keywords from ingested content.
3.  **Semantic Relationship Identification:**
    *   AI intelligently detects and maps meaningful relationships between extracted concepts, both within a single document and across an entire knowledge base.
4.  **Intelligent Summarization:**
    *   Generate concise, context-aware summaries for entire documents or specific selected sections.
5.  **Personal Knowledge Graph Visualization:**
    *   An interactive, dynamic frontend visualization of the interconnected concepts and their relationships, allowing users to explore their knowledge visually.
    *   Nodes represent concepts, edges represent relationships.
6.  **Natural Language Querying (NLQ):**
    *   Users can ask natural language questions about their ingested knowledge base (e.g., "What are the common arguments for X in documents A and B?", "How does concept Y relate to concept Z across all my notes?", "Summarize the findings on [topic] from my uploaded research papers.").
7.  **Contextual Insight Generation:**
    *   AI proactively suggests potential connections, contrasts, or novel insights based on the semantic relationships it has identified within the user's knowledge graph.
8.  **Automated & Manual Tagging:**
    *   AI suggests relevant tags for documents and concepts, with options for users to add or modify tags manually.
9.  **User Authentication & Authorization:**
    *   Secure user accounts to manage and personalize individual knowledge bases.

### User Interface & Experience:
*   Intuitive dashboard for managing documents and insights.
*   Document viewer with highlighting and annotation capabilities.
*   Search and filter functionality for documents and concepts.

# 4. Tech Stack

*   **Frontend:**
    *   **React.js:** For building a dynamic and responsive user interface.
    *   **Vite:** Fast development server and build tool for React.
    *   **Tailwind CSS:** Utility-first CSS framework for rapid and consistent styling.
    *   **Zustand / React Query:** For efficient state management and data fetching/caching.
    *   **ReactFlow / d3.js:** For interactive and customizable knowledge graph visualization.
*   **Backend:**
    *   **Node.js (Express.js):** Robust and scalable server-side framework.
    *   **Mongoose:** ODM (Object Data Modeling) for MongoDB interactions.
    *   **JWT (JSON Web Tokens):** For secure user authentication and authorization.
    *   **`pdf-parse`, `mammoth`:** Libraries for parsing PDF and DOCX files.
*   **Databases:**
    *   **MongoDB:** NoSQL database for storing user data, document metadata, extracted concepts (as structured data), and relationship details.
    *   **Vector Database (e.g., Pinecone, Weaviate, or Qdrant):** For storing vector embeddings of document chunks and concepts, enabling efficient semantic search and RAG (Retrieval Augmented Generation).
*   **AI/LLM Integration:**
    *   **Google Gemini API / OpenAI API (GPT Models):** For core AI functionalities like text embedding generation, concept extraction, summarization, relationship identification, and natural language query processing (RAG).
*   **Deployment (Example):**
    *   **Frontend:** Vercel / Netlify
    *   **Backend:** Render / AWS EC2 / DigitalOcean Droplet

# 5. Folder Structure

```
synapseforge/
├── client/                     # React Frontend Application
│   ├── public/                 # Static assets
│   ├── src/
│   │   ├── assets/             # Images, icons, fonts
│   │   ├── components/         # Reusable UI components
│   │   │   ├── common/         # Generic components (Button, Modal)
│   │   │   ├── ui/             # Tailwind CSS styled primitives
│   │   │   └── graph/          # Components specifically for graph visualization
│   │   ├── contexts/           # React Contexts (e.g., AuthContext, DocumentContext)
│   │   ├── hooks/              # Custom React Hooks (e.g., useAuth, useDocuments)
│   │   ├── pages/              # Top-level page components (views)
│   │   │   ├── Auth/           # Login, Register
│   │   │   ├── Dashboard/      # Main user dashboard
│   │   │   ├── DocumentView/   # Specific document detailed view
│   │   │   ├── KnowledgeGraph/ # Interactive graph view
│   │   │   └── Settings/       # User settings
│   │   ├── services/           # Frontend API interaction functions
│   │   ├── store/              # Zustand store definitions (if used over Context/React Query)
│   │   ├── utils/              # Frontend utility functions (e.g., date formatting)
│   │   ├── App.jsx             # Main application component
│   │   ├── main.jsx            # Entry point for React app
│   │   └── index.css           # Global styles and Tailwind CSS directives
│   ├── .env.example
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.js
│   └── vite.config.js
│
├── server/                     # Node.js Backend Application
│   ├── config/                 # Configuration files
│   │   ├── db.js               # Database connection
│   │   └── config.js           # Environment variables, constants
│   ├── controllers/            # Request handlers / Business logic
│   │   ├── authController.js
│   │   ├── documentController.js
│   │   ├── knowledgeController.js
│   │   └── queryController.js
│   ├── middlewares/            # Express middlewares
│   │   ├── authMiddleware.js   # JWT authentication
│   │   └── errorHandler.js     # Centralized error handling
│   ├── models/                 # Mongoose schemas
│   │   ├── User.js
│   │   ├── Document.js
│   │   ├── Concept.js          # (Representing extracted entities/concepts)
│   │   └── Relationship.js     # (Representing connections between concepts)
│   ├── routes/                 # API route definitions
│   │   ├── authRoutes.js
│   │   ├── documentRoutes.js
│   │   ├── knowledgeRoutes.js
│   │   └── queryRoutes.js
│   ├── services/               # Core AI and data processing logic
│   │   ├── llmService.js       # Interface to Gemini/OpenAI API
│   │   ├── embeddingService.js # Handles text chunking and embedding generation
│   │   ├── vectorDbService.js  # Interacts with the Vector Database
│   │   ├── documentProcessor.js # Handles file parsing (PDF, DOCX)
│   │   └── insightGenerator.js # Logic for contextual insight generation
│   ├── utils/                  # Backend utility functions
│   ├── app.js                  # Main Express application setup
│   ├── server.js               # Entry point to start the server
│   ├── .env.example
│   └── package.json
│
├── .env.example                # Global environment variables example
└── README.md                   # Project README
```

# 6. Architecture

1.  **Client-Side (Frontend - React):**
    *   **User Interface:** Built with React and styled using Tailwind CSS for a modern, responsive design.
    *   **Interaction:** Handles all user input, displays documents, the interactive knowledge graph, query results, and insights.
    *   **State Management:** Uses Zustand or React Query for efficient global state management, data fetching, and caching, ensuring a smooth user experience.
    *   **API Communication:** Makes asynchronous HTTP requests to the Node.js backend using `fetch` or `axios` to retrieve and send data.
    *   **Graph Visualization:** Employs `ReactFlow` or `d3.js` to render the dynamic and interactive knowledge graph, allowing users to zoom, pan, and click on nodes/edges for details.

2.  **Server-Side (Backend - Node.js/Express):**
    *   **API Gateway:** Express.js acts as the central hub, defining RESTful API endpoints for authentication, document management, knowledge processing, and querying.
    *   **Authentication & Authorization:** Implements JWT-based security to protect routes, ensuring only authenticated users can access and manage their knowledge.
    *   **Document Ingestion Pipeline:**
        *   Receives uploaded files or URLs.
        *   `documentProcessor.js` parses the content into raw text.
        *   This text is then passed to `embeddingService.js`.
    *   **AI Orchestration (`llmService.js`):**
        *   Acts as the primary interface to the Gemini/OpenAI API.
        *   Handles API key management, rate limiting, and structured prompt engineering.
        *   Invokes LLM for tasks like concept extraction, relationship identification, summarization, and query interpretation.
    *   **Data Processing & Storage:**
        *   `embeddingService.js`: Chunks the processed text, generates vector embeddings using the LLM's embedding model, and sends them to the Vector Database.
        *   `knowledgeController.js`: Manages the storage of document metadata, extracted concepts, and identified relationships in MongoDB.
        *   `vectorDbService.js`: Manages interactions with the chosen Vector Database (Pinecone/Weaviate/Qdrant) for storing and retrieving vector embeddings.
    *   **Query Engine (`queryController.js`):**
        *   Receives natural language queries from the frontend.
        *   Uses `llmService.js` to understand the query and generate an embedding for it.
        *   Performs a semantic similarity search in the Vector Database to retrieve the most relevant document chunks/concepts (RAG - Retrieval Augmented Generation).
        *   Feeds the retrieved context along with the original query back to the LLM to generate accurate and contextual answers.

3.  **Databases:**
    *   **MongoDB:** Stores structured data: user accounts, document metadata (title, original filename, upload date, associated user ID), extracted concepts (with properties like type, source document IDs), and explicit relationships (e.g., Concept A `relates_to` Concept B, `is_a` Concept C). This provides a flexible schema for evolving knowledge structures.
    *   **Vector Database (Pinecone/Weaviate/Qdrant):** Stores high-dimensional vector embeddings of document chunks and extracted concepts. This is critical for:
        *   **Semantic Search:** Efficiently finding text chunks or concepts semantically similar to a user's query.
        *   **RAG (Retrieval Augmented Generation):** Providing relevant context to the LLM when answering natural language queries, ensuring responses are grounded in the user's personal knowledge base.

4.  **AI/LLM Integration (Gemini/OpenAI):**
    *   **Embeddings:** Generates vector representations of text for semantic search and similarity.
    *   **Text Processing:** Extracts key information (entities, concepts, keywords), identifies relationships between them, and generates summaries.
    *   **Natural Language Understanding:** Interprets user queries, allowing the system to understand intent and retrieve relevant information.
    *   **Generative AI:** Forms coherent and contextual answers to user questions and generates proactive insights based on the retrieved information.

**Data Flow Example (Document Ingestion & Knowledge Graph Update):**
1.  User uploads a PDF file via the React Frontend.
2.  Frontend sends the PDF file (multipart/form-data) to the `/api/documents/upload` endpoint on the Node.js Backend.
3.  `documentController` receives the file, stores it temporarily, and calls `documentProcessor.js` to extract raw text content.
4.  The extracted raw text is then chunked into smaller, manageable pieces by `embeddingService.js`.
5.  `embeddingService.js` sends these text chunks to the LLM API (Gemini/OpenAI) to generate vector embeddings.
6.  The embeddings are then stored in the Vector Database by `vectorDbService.js`, indexed by a unique ID and associated with the original document.
7.  Simultaneously, the raw text (or selected chunks) is sent to `llmService.js` for **concept extraction**, **relationship identification**, and **summarization**.
8.  The extracted concepts (e.g., "AI", "Machine Learning", "Neural Networks") and identified relationships (e.g., "AI `encompasses` Machine Learning") are then stored in MongoDB by `knowledgeController.js`, linked to the original document and user.
9.  The Backend sends a success response to the Frontend, including any immediate summaries or status updates.
10. The Frontend updates the user's dashboard, showing the newly processed document. When the user navigates to the Knowledge Graph view, the Frontend fetches the concepts and relationships from MongoDB and visualizes them using `ReactFlow`/`d3.js`.

# 7. Future Scope

1.  **Collaborative Knowledge Bases:** Enable users to share documents, concepts, and relationships, fostering collaborative learning and research environments.
2.  **Browser Extension:** Develop a browser extension to seamlessly capture web content (articles, selected text) directly into SynapseForge with a single click.
3.  **Multimedia Content Ingestion:** Extend support to ingest and analyze content from images (OCR), audio (transcription), and video (transcription + summary).
4.  **Proactive Learning Recommendations:** Based on the user's existing knowledge graph, query history, and learning goals, the AI could proactively suggest relevant documents, concepts, or areas for further exploration.
5.  **Advanced Knowledge Graph Analytics:** Implement features like pathfinding between concepts, community detection, and influence analysis within the knowledge graph.
6.  **Export/Import Functionality:** Allow users to export their knowledge graphs or specific insights in various formats (e.g., JSON, GraphML, Markdown, PDF) and import existing knowledge structures.
7.  **Version Control for Knowledge:** Track changes and evolutions of concepts and relationships over time, allowing users to view historical states of their knowledge base.
8.  **Contextual Annotation & Highlights:** Enable users to highlight text within documents and ask the AI to explain, summarize, or connect highlighted sections to existing knowledge.
9.  **Integration with External Tools:** Connect with popular note-taking apps (e.g., Obsidian, Notion), task managers, or research platforms for a more integrated workflow.
10. **Mobile Application:** Develop native iOS and Android applications for on-the-go knowledge management and querying.

# 8. Complete README.md in Markdown

```markdown
# SynapseForge: AI-Powered Knowledge Weaver

## Table of Contents

1.  [Introduction](#1-introduction)
2.  [Problem Statement](#2-problem-statement)
3.  [Features](#3-features)
4.  [Tech Stack](#4-tech-stack)
5.  [Architecture](#5-architecture)
6.  [Folder Structure](#6-folder-structure)
7.  [Setup and Installation](#7-setup-and-installation)
    *   [Prerequisites](#prerequisites)
    *   [Environment Variables](#environment-variables)
    *   [Frontend Setup](#frontend-setup)
    *   [Backend Setup](#backend-setup)
8.  [Usage](#8-usage)
9.  [Future Scope](#9-future-scope)
10. [Contributing](#10-contributing)
11. [License](#11-license)
12. [Acknowledgements](#12-acknowledgements)

---

## 1. Introduction

SynapseForge is an innovative AI-powered application designed to revolutionize personal knowledge management. It acts as an intelligent assistant that transforms fragmented, unstructured information from various sources (documents, notes, web articles) into a cohesive, interconnected, and queryable knowledge base. By leveraging advanced AI models, SynapseForge extracts key concepts, identifies semantic relationships, and visualizes them as an interactive knowledge graph, enabling users to discover deeper insights and retrieve information through natural language queries.

## 2. Problem Statement

In today's information-rich environment, individuals frequently grapple with overwhelming amounts of data from disparate sources. This data often remains isolated, hindering effective synthesis, cross-referencing, and insight generation. Conventional note-taking and document management tools are passive, demanding substantial manual effort for organization, connection-making, and retrieval, which often results in overlooked connections and inefficient knowledge utilization. SynapseForge addresses this challenge by providing an intelligent system capable of automatically structuring and interconnecting personal information, thus enhancing comprehension and accelerating decision-making processes.

## 3. Features

### Core Functionality:
*   **Multi-format Document Ingestion:** Upload PDFs, TXT, DOCX, Markdown, or paste web article URLs for automated content processing.
*   **Automated Key Concept & Entity Extraction:** AI identifies and extracts core concepts, named entities (people, organizations), and keywords from your content.
*   **Semantic Relationship Identification:** AI intelligently detects and maps meaningful relationships between concepts, both within individual documents and across your entire knowledge base.
*   **Intelligent Summarization:** Generate concise, context-aware summaries for entire documents or selected sections.
*   **Personal Knowledge Graph Visualization:** An interactive, dynamic frontend visualization representing interconnected concepts and their relationships, allowing for intuitive knowledge exploration.
*   **Natural Language Querying (NLQ):** Ask questions about your ingested knowledge base in plain English (e.g., "What are the common arguments for X in documents A and B?", "How does concept Y relate to concept Z across all my notes?").
*   **Contextual Insight Generation:** AI proactively suggests potential connections, contrasts, or novel insights derived from the semantic relationships within your knowledge graph.
*   **Automated & Manual Tagging:** AI proposes relevant tags for documents and concepts, with full user control for modifications.
*   **User Authentication & Authorization:** Secure user accounts to manage and personalize individual knowledge bases.

### User Interface & Experience:
*   Intuitive dashboard for managing documents and insights.
*   Integrated document viewer with highlighting and annotation capabilities.
*   Comprehensive search and filter functionality for documents and concepts.

## 4. Tech Stack

*   **Frontend:**
    *   [**React.js**](https://react.dev/): A declarative, component-based JavaScript library for building user interfaces.
    *   [**Vite**](https://vitejs.dev/): Next-generation frontend tooling for a blazing fast development experience.
    *   [**Tailwind CSS**](https://tailwindcss.com/): A utility-first CSS framework for rapidly building custom designs.
    *   [**Zustand**](https://zustand-demo.pmnd.rs/) / [**React Query**](https://tanstack.com/query/latest): For efficient state management and server-state synchronization.
    *   [**ReactFlow**](https://reactflow.dev/) / [**d3.js**](https://d3js.org/): For interactive and customizable knowledge graph visualization.
*   **Backend:**
    *   [**Node.js**](https://nodejs.org/): JavaScript runtime for server-side logic.
    *   [**Express.js**](https://expressjs.com/): Fast, unopinionated, minimalist web framework for Node.js.
    *   [**Mongoose**](https://mongoosejs.com/): MongoDB object data modeling (ODM) for Node.js.
    *   [**JWT (JSON Web Tokens)**](https://jwt.io/): For secure user authentication.
    *   [**pdf-parse**](https://www.npmjs.com/package/pdf-parse), [**mammoth.js**](https://www.npmjs.com/package/mammoth): Libraries for parsing PDF and DOCX files respectively.
*   **Databases:**
    *   [**MongoDB**](https://www.mongodb.com/): A NoSQL document database for flexible storage of user data, document metadata, and structured concept definitions.
    *   [**Vector Database (e.g., Pinecone, Weaviate, or Qdrant)**](https://www.pinecone.io/learn/vector-database/): For storing vector embeddings crucial for semantic search and Retrieval Augmented Generation (RAG).
*   **AI/LLM Integration:**
    *   [**Google Gemini API**](https://ai.google.dev/) / [**OpenAI API (GPT Models)**](https://openai.com/docs/api-reference): Provides the core AI capabilities for text embedding, concept extraction, summarization, relationship identification, and natural language query processing.

## 5. Architecture

SynapseForge employs a robust microservice-oriented architecture with a clear separation of concerns:

```
+----------------+      +---------------------+      +-------------------+
|                |      |                     |      |                   |
|  React Client  |----->|  Node.js Backend    |<---->|     LLM API       |
| (Vite, Tailwind)| HTTP | (Express.js, JWT)   |      | (Gemini/OpenAI)   |
|                |      |                     |      |                   |
+----------------+      +---------+-----------+      +--------^----------+
                              |         ^                     |
                              |         |                     | Embeddings
                              v         |                     | Generation
                        +-----+---------+-----+         +-----+-----+
                        |                     |         |           |
                        |     MongoDB         |<------->| Vector DB |
                        | (User, Docs, Concepts)|         | (Embeddings)|
                        |                     |         |           |
                        +---------------------+         +-----------+
```

1.  **Client-Side (React Frontend):**
    *   The user's primary interface, built with React and styled with Tailwind CSS for a modern, responsive experience.
    *   Handles all user interactions, visualizes the knowledge graph (using `ReactFlow` or `d3.js`), displays documents, query results, and insights.
    *   Communicates with the Node.js backend via RESTful API calls.
    *   Manages local state and fetches/caches data efficiently using Zustand or React Query.

2.  **Server-Side (Node.js Backend):**
    *   Acts as the central API gateway using Express.js.
    *   **Authentication & Authorization:** Secures user access with JWT.
    *   **Document Ingestion Pipeline:** Processes uploaded documents/URLs, extracts raw text (`documentProcessor.js`).
    *   **AI Orchestration (`llmService.js`):** Interfaces with the Gemini/OpenAI API for:
        *   Generating text embeddings.
        *   Extracting concepts and identifying relationships.
        *   Summarizing content.
        *   Interpreting natural language queries.
    *   **Data Processing & Storage:**
        *   `embeddingService.js`: Chunks text and sends to LLM for vector generation; stores embeddings in the Vector Database.
        *   `knowledgeController.js`: Manages structured data (document metadata, concepts, relationships) in MongoDB.
        *   `vectorDbService.js`: Handles all interactions with the Vector Database.
    *   **Query Engine (`queryController.js`):** Interprets NLQ, performs semantic searches in the Vector DB (RAG), and uses the LLM to generate grounded answers.

3.  **Databases:**
    *   **MongoDB:** Stores structured information such as user profiles, document metadata, extracted concepts (their properties, source documents), and explicit relationships between concepts.
    *   **Vector Database (e.g., Pinecone/Weaviate/Qdrant):** Crucial for high-performance semantic search. It stores high-dimensional vector embeddings of document chunks and concepts, enabling efficient retrieval of semantically similar content for RAG.

4.  **AI/LLM Integration (Gemini/OpenAI):**
    *   The "brain" of SynapseForge, providing core intelligence for all text-based processing:
        *   **Embeddings:** Converts text into numerical vectors for similarity comparisons.
        *   **Text Processing:** Extracts key information, identifies relationships, and generates summaries.
        *   **Natural Language Understanding:** Interprets user queries and facilitates context-aware search.
        *   **Generative AI:** Crafts coherent and accurate answers to user questions and generates insightful connections.

## 6. Folder Structure

```
synapseforge/
├── client/                     # React Frontend Application
│   ├── public/                 # Static assets
│   ├── src/
│   │   ├── assets/             # Images, icons, fonts
│   │   ├── components/         # Reusable UI components
│   │   │   ├── common/         # Generic components (Button, Modal)
│   │   │   ├── ui/             # Tailwind CSS styled primitives
│   │   │   └── graph/          # Components specifically for graph visualization
│   │   ├── contexts/           # React Contexts (e.g., AuthContext, DocumentContext)
│   │   ├── hooks/              # Custom React Hooks (e.g., useAuth, useDocuments)
│   │   ├── pages/              # Top-level page components (views)
│   │   │   ├── Auth/           # Login, Register
│   │   │   ├── Dashboard/      # Main user dashboard
│   │   │   ├── DocumentView/   # Specific document detailed view
│   │   │   ├── KnowledgeGraph/ # Interactive graph view
│   │   │   └── Settings/       # User settings
│   │   ├── services/           # Frontend API interaction functions
│   │   ├── store/              # Zustand store definitions (if used over Context/React Query)
│   │   ├── utils/              # Frontend utility functions (e.g., date formatting)
│   │   ├── App.jsx             # Main application component
│   │   ├── main.jsx            # Entry point for React app
│   │   └── index.css           # Global styles and Tailwind CSS directives
│   ├── .env.example
│   ├── package.json
│   ├── postcss.config.js
│   ├── tailwind.config.js
│   └── vite.config.js
│
├── server/                     # Node.js Backend Application
│   ├── config/                 # Configuration files
│   │   ├── db.js               # Database connection
│   │   └── config.js           # Environment variables, constants
│   ├── controllers/            # Request handlers / Business logic
│   │   ├── authController.js
│   │   ├── documentController.js
│   │   ├── knowledgeController.js
│   │   └── queryController.js
│   ├── middlewares/            # Express middlewares
│   │   ├── authMiddleware.js   # JWT authentication
│   │   └── errorHandler.js     # Centralized error handling
│   ├── models/                 # Mongoose schemas
│   │   ├── User.js
│   │   ├── Document.js
│   │   ├── Concept.js          # (Representing extracted entities/concepts)
│   │   └── Relationship.js     # (Representing connections between concepts)
│   ├── routes/                 # API route definitions
│   │   ├── authRoutes.js
│   │   ├── documentRoutes.js
│   │   ├── knowledgeRoutes.js
│   │   └── queryRoutes.js
│   ├── services/               # Core AI and data processing logic
│   │   ├── llmService.js       # Interface to Gemini/OpenAI API
│   │   ├── embeddingService.js # Handles text chunking and embedding generation
│   │   ├── vectorDbService.js  # Interacts with the Vector Database
│   │   ├── documentProcessor.js # Handles file parsing (PDF, DOCX)
│   │   └── insightGenerator.js # Logic for contextual insight generation
│   ├── utils/                  # Backend utility functions
│   ├── app.js                  # Main Express application setup
│   ├── server.js               # Entry point to start the server
│   ├── .env.example
│   └── package.json
│
├── .env.example                # Global environment variables example
└── README.md                   # Project README
```

## 7. Setup and Installation

Follow these steps to get SynapseForge up and running on your local machine.

### Prerequisites

*   [Node.js](https://nodejs.org/en/download/) (v18.x or higher recommended)
*   [npm](https://www.npmjs.com/get-npm) or [Yarn](https://yarnpkg.com/getting-started/install) package manager
*   [MongoDB](https://docs.mongodb.com/manual/installation/) instance (local or cloud-hosted like MongoDB Atlas)
*   Access to [Google Gemini API](https://ai.google.dev/) or [OpenAI API](https://platform.openai.com/docs/api-reference)
*   Account with a [Vector Database provider](https://www.pinecone.io/start/) (e.g., Pinecone, Weaviate, Qdrant)

### Environment Variables

Create a `.env` file in both the `client/` and `server/` directories, and also a root `.env` file if you prefer (though separate ones are recommended for clarity). Refer to `.env.example` files.

#### `server/.env` example:

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/synapseforge
JWT_SECRET=your_jwt_secret_key_here
GEMINI_API_KEY=your_gemini_api_key_here
OPENAI_API_KEY=your_openai_api_key_here
# Choose one LLM provider and configure its key.
# Vector DB configuration (example for Pinecone)
VECTOR_DB_API_KEY=your_vector_db_api_key
VECTOR_DB_ENVIRONMENT=your_vector_db_environment
VECTOR_DB_INDEX_NAME=synapseforge-index
```

#### `client/.env` example:

```env
VITE_API_BASE_URL=http://localhost:5000/api
```

### Frontend Setup

1.  Navigate to the `client` directory:
    ```bash
    cd client
    ```
2.  Install dependencies:
    ```bash
    npm install
    # or yarn install
    ```
3.  Start the development server:
    ```bash
    npm run dev
    # or yarn dev
    ```
    The frontend should now be running on `http://localhost:5173` (or another port specified by Vite).

### Backend Setup

1.  Navigate to the `server` directory:
    ```bash
    cd server
    ```
2.  Install dependencies:
    ```bash
    npm install
    # or yarn install
    ```
3.  Ensure your MongoDB instance is running and accessible via the `MONGODB_URI` in your `.env` file.
4.  Start the backend server:
    ```bash
    npm start
    # or yarn start
    ```
    The backend should now be running on `http://localhost:5000` (or the port specified in your `.env`).

## 8. Usage

1.  **Register/Login:** Access the frontend application in your browser (e.g., `http://localhost:5173`) and create a new account or log in.
2.  **Upload Documents:** Navigate to the dashboard or upload section to ingest your PDFs, DOCX files, TXT files, Markdown files, or paste web article URLs.
3.  **Explore Knowledge Graph:** After processing, visit the "Knowledge Graph" section to visualize the extracted concepts and their relationships. Interact with nodes and edges to view details.
4.  **Query Your Knowledge:** Use the natural language query interface to ask questions about your documents and insights.
5.  **View Insights:** Discover AI-generated summaries and contextual insights derived from your interconnected knowledge.

## 9. Future Scope

*   **Collaborative Knowledge Bases:** Allow users to share and collaboratively build knowledge graphs.
*   **Browser Extension:** Integrate with web browsers to easily capture web content directly into SynapseForge.
*   **Multimedia Support:** Ingest and analyze content from images (OCR), audio (transcription), and video (transcription + summary).
*   **Proactive Learning Suggestions:** Based on the user's knowledge graph and queries, suggest related topics or documents.
*   **Export/Import Functionality:** Export knowledge graphs or summaries in various formats (e.g., JSON, GraphML, Markdown).
*   **Advanced Visualization:** More interactive and customizable graph visualizations, including filtering, clustering, and temporal views.
*   **Version Control & History:** Track changes to the knowledge graph and documents over time, allowing rollback.
*   **Mobile Application:** Native mobile applications for iOS and Android.

## 10. Contributing

Contributions are welcome! If you have suggestions for improvements, new features, or bug fixes, please open an issue or submit a pull request.

## 11. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 12. Acknowledgements

*   Developed as a final-year B.Tech CSE project.
*   Special thanks to Google Gemini and OpenAI for their powerful API services.
*   Built with the amazing React, Node.js, and Tailwind CSS communities.
```