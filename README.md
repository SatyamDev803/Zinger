The Vibe Frontend: Development Roadmap
Module 1: Foundation, Theming & Wallet Connection
Goal: To establish the core structure, visual identity, and Web3 connectivity of the app. This is the skeleton upon which everything else is built.

Key Features:

Clean up default Next.js project files.

Set up global CSS for our Pink/White theme and dark mode.

Create a reusable glass-card CSS utility for our glassmorphism design.

Build the main layout.tsx with a persistent Sidebar for navigation.

Integrate RainbowKit to provide a beautiful and simple "Connect Wallet" button in the sidebar.

Create a UserSync component that automatically creates a user in our backend via the /api/users endpoint the first time they connect their wallet.

Milestone: A running application with a stunning, consistent layout. A user can connect their MetaMask wallet, and their account is silently created in our database.

Module 2: The Swipe Experience (Homepage)
Goal: To build the primary user interaction—the "dating app" style swiping interface for discovering other users.

Key Features:

A SwipeContainer component on the homepage (/).

Use the Swiper.js library with the "Cards Effect" to create a smooth, touch-friendly swiping experience.

Profile cards that display a user's picture, name, and bio.

Backend Integration:

GET /api/users to fetch a list of potential profiles to show in the swipe container.

POST /api/matches is triggered on a "swipe right" to create a pending match request between the current user and the swiped user.

Milestone: A fully interactive homepage where a user can swipe through profiles, and their right-swipes are registered as match attempts in the backend.

Module 3: Matches & Chat
Goal: To allow users to see who they've successfully matched with and simulate a conversation.

Key Features:

A Matches Page (/matches) that displays a list of all users where the match status is "accepted".

A dynamic Chat Page (/matches/[id]) that shows a simulated chat interface between the current user and their match.

Backend Integration:

GET /api/matches/user/:userId to fetch the list of accepted matches for the currently connected user.

Milestone: A user can navigate from the sidebar to see a list of their matches and click on any match to open a beautiful, albeit simulated, chat screen.

Module 4: Events & Community
Goal: To build out the group social features of the platform, allowing users to find and participate in events.

Key Features:

An Events Page (/events) that displays all available events in stylish glass-card components.

A "Join Event" button on each card.

A view to see who is already participating in an event.

Backend Integration:

GET /api/events to fetch and display the list of all events.

POST /api/events/:eventId/join triggered when a user clicks the "Join" button.

DELETE /api/events/:eventId/leave for when a user decides to leave an event.

Milestone: A fully functional Events page where users can browse upcoming events and manage their attendance, with changes reflected in the database.

Module 5: User Settings & Profile Management
Goal: To give users control over their own identity on the platform.

Key Features:

A Settings Page (/settings) with a simple, clean form.

Form fields for users to update their username and bio.

Backend Integration:

PUT /api/users/:id to send the updated form data and save it to the user's profile in the database.

Milestone: A settings page where a user can edit their profile information and see those changes persist.

Module 6: Premium Membership (The Web3 "Wow" Factor)
Goal: To implement the core Web3 feature that will win the hackathon—allowing users to purchase a premium membership using your live smart contract.

Key Features:

A PremiumButton component placed prominently in the UI (e.g., in the sidebar or on the settings page).

Clear UI feedback for the transaction lifecycle (e.g., "Confirm in wallet...", "Processing...", "Success!").

A "Premium ✨" badge that conditionally appears next to the user's name throughout the app (on their profile card, in the matches list, etc.).

Web3 Integration:

Use the useWriteContract hook from wagmi to call the purchaseMembership function on your deployed VibePayments.sol smart contract.

The transaction will send 10 ARB (from the user's testnet funds) to the contract.

Milestone: The "magic moment" of your demo: a user clicks a button, approves a real transaction in MetaMask, and moments later, their isPremium status is automatically updated in the UI, unlocking a visual badge. This demonstrates a complete, end-to-end Web3 integration.