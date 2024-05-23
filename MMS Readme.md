# sp-mms-frontend

Repository for the MMS Frontend code.
## Local installation and development

Clone the repository at https://github.com/Squad-C/sp-mms-api-gateway
And follow the instructions in the README file to run a local version of the api gateway.
## Branching
`development` - branch for development
`main` - branch for production
`[user]/MMS-[issue_number]-[issue_description]` - branch for issues

Branches are only to created when there is already an existing issue for the task. 
The syntax for the branch naming requires the user name, project name, issue number, and description:
  `[user]/MMS-[issue_number]-[issue_description]` 
Example:
  `jason/MMS-001-update-readme-file`
## File structure
```
sp-mms-frontend
└── public
└── src
  └── assets
  └── components
    └── layout
    └── parts
    └── templates
  └── context
  └── lib
  └── pages
  └── routes
  └── services
    └── api
    └── hooks
  └── utils
```
We are following modular organization where related files are grouped together within a directory. Here are how the files are organized:
- assets - for app assets like logo and images.
- components - split into three sub diecrtories. The `components/layout` is for defining page layouts like having a navbar header. The `components/parts` is for defining base components such as buttons, radio input, input fields, pills, etc. The `components/templates` is for templates that use multiple component parts such as Forms that use multiple fields and buttons.
- context - for defining React contexts and their respective providers. Essential for managing global state and making it accessible to compononents.
- lib - for libraries and modules. This includes organizing functionalities of i18n translations under the `lib/dict` directory. 
- pages - for defining the pages. 
- routes - for defining the routes that points to the pages/components
- services - split into two sub directories. The `services/api` is the directory for defining all API interactions with the backend endpoints. Meanwhile, the `services/hooks` is the directory for defining all the React hooks, queries, and custom hooks.
- utils - for utility functions utilized throughout the application.
### Pages
To create a `component` or `page`, create a folder that contains an `index.tsx` and (optional) `hooks.ts` file. The index.tsx file will serve as the main entry point and the hooks.ts file will be where we define the hooks and functions.
Example:
```
pages
└──my-page
    └──index.tsx
    └──hooks.ts
```
### Translations
The i18next package is used for translations. The i18n instance is defined in the `lib/dict/i18n.ts` file.  

To create an additional namespace for translations, create a new file for the english and deutsch version under the `lib/dict/en or lib/dict/de` directory. The file should export an object with a key-value pair for the translated text. Here's an example:
```
export default {
    "sample-key": "sample translation",
    "another-key": "another sample translation"
}
```

Then, in the `i18n.ts` file, add the namespace name in the array under the key - `ns`. 
```
i18n.use(initReactI18next)
    .use(LanguageDetector)
    .init({
        fallbackLng: 'en',
        resources,
        ns: ['common', 'auth', 'company', 'reference', 'new-namespace']
    })
```

In order to use the translation and its namespace (defaulted to `common`), import `t` from `i18next` and in the jsx, add the following code snippet:
```
return (
	 <div>
	   {t('sample-key', { ns: 'new-namespace' })} // 'sample translation'
	 </div>
 )
```
## Packages
- `tanstack-query`
  React Query, also known as Tanstack, makes fetching and managing data in React apps easy. It's great for caching data like lists. If your data isn't too complex, you can just call the API directly. 
- `react-hook-form`
  React Hook Form simplifies form validation in React applications. It streamlines the process of validating and handling form data.
- `zod`
  Zod is a TypeScript-first schema declaration and validation library. 
* `heroicons/react` 
  Heroicons is a library for adding icons in a React project. To use, just import the icon you need and use it directly in your JSX code. 
- `universal-cookie`
  Universal cookie is used for managing cookies in web applications. It provides functionality for creating, accessing, and storing cookies in the browser.
- `moment`
  Moment js makes it easy to format dates.