# UI Kit

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/fission-suite/blob/master/LICENSE)
[![Built by FISSION](https://img.shields.io/badge/⌘-Built_by_FISSION-purple.svg)](https://fission.codes)
[![Discord](https://img.shields.io/discord/478735028319158273.svg)](https://discord.gg/zAQBDEq)
[![Discourse](https://img.shields.io/discourse/https/talk.fission.codes/topics)](https://talk.fission.codes)

__The Fission UI Kit__,  
_designed to be used with [Tailwind CSS](https://tailwindcss.com)._

🎨 [Styleguide](https://kit.fission.app)  
📖 [Documentation](https://kit.fission.app/docs/)



## Getting Started

### Step one, install dependencies.

* `npm install @fission-suite/kit`
* `npm install tailwindcss`
* Copy the font files.  
  `npx copy-fission-fonts ./vendor/fonts/ --woff2`
* Copt the images.
  `npx copy-fission-images ./vendor/images/`


### Step two, configure Tailwind CSS.

We need to configure Tailwind CSS to use the Fission colors, fonts and other things.

```js
import plugin from "tailwindcss/plugin"
import * as kit from "@fission-suite/kit"
// or kit = require("@fission-suite/kit")

export default {
  purge: [
    ...kit.tailwindPurgeList()
  ],

  theme: {
    colors: kit.dasherizeObjectKeys(kit.colors),
    fontFamily: kit.fonts,

    extend: {
      fontSize: kit.fontSizes
    }
  },

  plugins: [
    plugin(function({ addBase }) {
      // this `fontsPath` will be the relative path
      // to the fonts from the generated stylesheet
      kit.fontFaces({ fontsPath: "/fonts/" }).forEach(fontFace => {
        addBase({ "@font-face": fontFace })
      })
    })
  ]
}
```

See the [`guide`](./guide/) for an example configuration, and how to use the Elm library.


### Step three, use the component library.

#### React

```shell
npm install @fission-suite/kit
```

```js
import { SignInButton } from "@fission-suite/kit/components/react"

<SignInButton
  className="bg-base-900 text-base-50 dark:bg-base-100 dark:text-base-900"
  onClick={() => webnative.redirectToLobby(PERMISSIONS)}
/>
```

📖 [Documentation](https://kit.fission.app/docs/react/)

#### Elm

```shell
elm install fission-suite/kit
```

```elm
import Kit.Components

Kit.Components.signIn [ class "bg-purple text-white text-opacity-90" ]
```

📖 [Documentation](https://package.elm-lang.org/packages/fission-suite/kit/latest/)
