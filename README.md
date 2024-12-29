## Hi there 👋

<!--
**DarkAngel35-commits/DarkAngel35-commits** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
android {
    defaultConfig {
        manifestPlaceholders["hostName"] = "www.example.com"
        ...
    }
    buildTypes {
        getByName("release") {
            isMinifyEnabled = true
            proguardFiles(getDefaultProguardFile("proguard-android.txt"), "proguard-rules.pro")
        }

        getByName("debug") {
            applicationIdSuffix = ".debug"
            isDebuggable = true
        }

        /**
         * The `initWith` property lets you copy configurations from other build types,
         * then configure only the settings you want to change. This one copies the debug build
         * type, and then changes the manifest placeholder and application ID.
         */
        create("staging") {
            initWith(getByName("debug"))
            manifestPlaceholders["hostName"] = "internal.example.com"
            applicationIdSuffix = ".debugStaging"
        }
    }
}
