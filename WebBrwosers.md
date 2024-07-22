### Web Browsers

---

#### Overview

Web browsers are pieces of softwares that facilliate the retrieval, display and interaction of webpage reooucres at your request. They provide functionalities such as playing a video, fetching a website and even better offering extensions that make life much easier.

---

#### UI

For browsers, it is weird that there is no standardized protocol that governs the user interfaces for them. However, there is some common UI components they share.  The list goes:

1. Address bar for inserting a URI
2. Back and forward buttons
3. Bookmarking options
4. Refresh and stop buttons for refreshing or stopping the loading of current documents
5. Home button that takes you to your home page

---

#### Infrastructure

1. **The user interface**: the part of brwoser you see minus the main window
2. **The browser engine**: connects actions between the UI and the rendering engine.
3. **The rendering engine**: responsible for displaying requested content.
4. **Networking**: for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
5. **UI backend**: used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses operating system user interface methods.
6. **JavaScript interpreter**. Used to parse and execute JavaScript code.
7. **Data storage**. This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem.