# Project Documentation

## Overview

This project is a web application built using React and TypeScript, featuring a responsive design and a theme-aware user interface. The application includes various components, including a footer, and utilizes React Router for client-side routing. The project is designed to provide users with an intuitive and visually appealing experience while navigating through different sections of the application.

## Table of Contents

- [Project Documentation](#project-documentation)
  - [Overview](#overview)
  - [Table of Contents](#table-of-contents)
  - [Technologies Used](#technologies-used)
  - [Installation](#installation)
  - [Project Structure](#project-structure)
  - [Components](#components)
  - [Routing](#routing)
  - [Theming](#theming)
  - [Styling](#styling)
  - [Usage](#usage)

## Technologies Used

- **React**: A JavaScript library for building user interfaces.
- **TypeScript**: A superset of JavaScript that adds static typing.
- **React Router**: A library for routing in React applications.
- **Tailwind CSS**: A utility-first CSS framework for styling.
- **SVG**: Scalable Vector Graphics for the application logo.

## Installation

To set up the project locally, follow these steps:

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Install the dependencies:

   ```bash
   npm install
   ```
   Start the development server:

   ```bash
   npm run dev
   ```
   Open your browser and navigate to http://localhost:6714 to view the application.

## Project Structure
The project is organized into the following structure:

   ```
   /car-bon-ui
   ┣ Docs/
   ┃ ┗ UI_Documentation.md
   ┣ public/
   ┃ ┣ car-bon-favicon.svg
   ┃ ┣ car-bon-icon-glow.svg
   ┃ ┣ car-bon-icon.svg
   ┃ ┣ car-bon-logo.svg
   ┃ ┣ splash.png
   ┃ ┗ vite.svg
   ┣ src/
   ┃ ┣ Contexts/
   ┃ ┃ ┗ UserContext.ts
   ┃ ┣ assets/
   ┃ ┃ ┣ car-bon-favicon.svg
   ┃ ┃ ┣ car-bon-icon.svg
   ┃ ┃ ┣ car-bon-logo.svg
   ┃ ┃ ┗ react.svg
   ┃ ┣ components/
   ┃ ┃ ┣ Charts/
   ┃ ┃ ┃ ┣ bar_chart.tsx
   ┃ ┃ ┃ ┗ line_chart.tsx
   ┃ ┃ ┣ Loader/
   ┃ ┃ ┃ ┗ Loader.tsx
   ┃ ┃ ┣ Pagination_wrapper/
   ┃ ┃ ┃ ┗ pagination.tsx
   ┃ ┃ ┣ PanelLayout/
   ┃ ┃ ┃ ┣ Layout.tsx
   ┃ ┃ ┃ ┣ PanelLayout.tsx
   ┃ ┃ ┃ ┣ collapsible_menu_button.tsx
   ┃ ┃ ┃ ┣ content_layout.tsx
   ┃ ┃ ┃ ┣ footer.tsx
   ┃ ┃ ┃ ┣ menu.tsx
   ┃ ┃ ┃ ┣ navbar.tsx
   ┃ ┃ ┃ ┣ sheet-menu.tsx
   ┃ ┃ ┃ ┣ sidebar.tsx
   ┃ ┃ ┃ ┣ sidebarToggle.tsx
   ┃ ┃ ┃ ┗ user-nav.tsx
   ┃ ┃ ┣ SelectBox/
   ┃ ┃ ┃ ┗ selectBoxComponent.tsx
   ┃ ┃ ┣ collapsible/
   ┃ ┃ ┃ ┗ Collapsible.tsx
   ┃ ┃ ┣ custom/
   ┃ ┃ ┃ ┗ kpi.tsx
   ┃ ┃ ┣ data-fetcher/
   ┃ ┃ ┃ ┗ DataFetcher.tsx
   ┃ ┃ ┣ hamburger-menu/
   ┃ ┃ ┃ ┗ HamburgerMenu.tsx
   ┃ ┃ ┣ menubar/
   ┃ ┃ ┃ ┗ Menubar.tsx
   ┃ ┃ ┣ phone-number-picker/
   ┃ ┃ ┃ ┗ PhoneNumberPicker.jsx
   ┃ ┃ ┣ rsuite/
   ┃ ┃ ┃ ┣ charts/
   ┃ ┃ ┃ ┃ ┗ Charts.tsx
   ┃ ┃ ┃ ┗ date-picker/
   ┃ ┃ ┃   ┗ DatePicker.tsx
   ┃ ┃ ┣ sidebar/
   ┃ ┃ ┃ ┣ CustomSidebar.tsx
   ┃ ┃ ┃ ┗ Navbar.tsx
   ┃ ┃ ┣ theme-toggle/
   ┃ ┃ ┃ ┗ ThemeToggle.tsx
   ┃ ┃ ┣ ui/
   ┃ ┃ ┃ ┣ avatar.tsx
   ┃ ┃ ┃ ┣ breadcrumb.tsx
   ┃ ┃ ┃ ┣ button.tsx
   ┃ ┃ ┃ ┣ card.tsx
   ┃ ┃ ┃ ┣ chart.tsx
   ┃ ┃ ┃ ┣ collapsible.tsx
   ┃ ┃ ┃ ┣ dropdown-menu.tsx
   ┃ ┃ ┃ ┣ menubar.tsx
   ┃ ┃ ┃ ┣ pagination.tsx
   ┃ ┃ ┃ ┣ resizable.tsx
   ┃ ┃ ┃ ┣ scroll-area.tsx
   ┃ ┃ ┃ ┣ select.tsx
   ┃ ┃ ┃ ┣ separator.tsx
   ┃ ┃ ┃ ┣ sheet.tsx
   ┃ ┃ ┃ ┣ skeleton.tsx
   ┃ ┃ ┃ ┗ tooltip.tsx
   ┃ ┃ ┣ user-manager/
   ┃ ┃ ┃ ┗ UserManager.tsx
   ┃ ┃ ┗ theme-provider.tsx
   ┃ ┣ config/
   ┃ ┃ ┗ menu.json
   ┃ ┣ lib/
   ┃ ┃ ┣ Encryption.ts
   ┃ ┃ ┣ menu-list.ts
   ┃ ┃ ┗ utils.ts
   ┃ ┣ pages/
   ┃ ┃ ┣ ClerkAuth.tsx
   ┃ ┃ ┣ ClerkDefault.tsx
   ┃ ┃ ┣ ClerkLogin.tsx
   ┃ ┃ ┣ Dashboard.tsx
   ┃ ┃ ┣ DeviceList.tsx
   ┃ ┃ ┣ Devices.tsx
   ┃ ┃ ┣ Home.tsx
   ┃ ┃ ┣ Landing.tsx
   ┃ ┃ ┣ Layout.tsx
   ┃ ┃ ┣ Login.tsx
   ┃ ┃ ┣ Logout.tsx
   ┃ ┃ ┗ Register.tsx
   ┃ ┣ providers/
   ┃ ┃ ┗ AuthProvider/
   ┃ ┃   ┗ auth.tsx
   ┃ ┣ routes/
   ┃ ┃ ┣ Breadcrumbs.tsx
   ┃ ┃ ┣ ProtectedRoute.tsx
   ┃ ┃ ┗ index.tsx
   ┃ ┣ types/
   ┃ ┃ ┣ UserDetails.ts
   ┃ ┃ ┗ date_range_type.ts
   ┃ ┣ App.css
   ┃ ┣ App.tsx
   ┃ ┣ index.css
   ┃ ┣ main.tsx
   ┃ ┗ vite-env.d.ts
   ┣ .env
   ┣ .eslintrc.cjs
   ┣ .gitignore
   ┣ README.md
   ┣ capacitor.config.ts
   ┣ components.json
   ┣ deploy_ui.sh
   ┣ global.d.ts
   ┣ index.html
   ┣ package.json
   ┣ postcss.config.js
   ┣ tailwind.config.js
   ┣ tsconfig.app.json
   ┣ tsconfig.json
   ┣ tsconfig.node.json
   ┣ vite.config.ts
   ┗ webpack.config.js
   ```

## Components
The application consists of several reusable components, including:

**Charts** : The Component that renders charts  
**Loader** : The Component that rendersa loader animation  
**Pagination_wrapper** : A wrapper over ShadCN Ui Components to modify and customize the pagination component  
**PanelLayout** : A generic component for rendering the layout of the Application  
**SelectBox** : A wrapper component over ShadCn Dropdown Select Box component  
**collapsible** : A Custom component for Sidebar  
**custom** : some cutom components like KPI metrics  
**data-fetcher** : the main component which fetches data from API.  
**hamburger-menu** : Hamburger menu to trigger opening and closing of Sidebar.  
**rsuite** : wrappers for generic components from rsuite.  
**theme-toggle** : Theme toggle component.  
**ui** : Generic Shad Cn UI components.  
**theme-provider.tsx** : Theme provider base context component.  
**Other Page Components**: Various components representing different pages in the application (e.g., Home, Dashboard, Account).  

## Routing
The application uses React Router for client-side routing. The main routes typically include:

*  `/`: The root route, which renders the Home page.
*  `/dashboard`: The dashboard route, which renders the Dashboard page.
*  `/account`: The Account route, which renders the Account management page
*  `/login`: Page for Login (Clerk Login Route)
*  `/register`: Page for Register (Clerk Register Route)
*  `/devices`: Page for user Devices and current metrics.

Routes are defined in the routes index file (`routes/index.tsx`).

## Theming
The application supports light and dark themes. The theme can be toggled using the `theme-toggle` component, which provides the current theme context to components. The components adjust their styles based on the selected theme.

## Styling
The project uses Tailwind CSS for styling. This utility-first CSS framework allows for rapid styling directly within the JSX code. Custom styles can also be added as needed.

## Usage
for usage guidelines of the application, refer [user-manual](./user-manual.md)
