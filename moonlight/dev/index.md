### Introduction

Moonlight is built in a modular and expandable way. To extend moonlights functionalities you have two options. MoonlightFeatures und MoonlightPlugins.

**Plugins**:
MoonlightPlugins are a minimal dll which is implementing interfaces provided by the moonlight features and registered through the plugin api management service. [Create your own plugin](/moonlight/dev/plugins)

**Features**
MoonlightFeatures are a dll and optional a asset folder which have access to moonlights feature apis allowing to execute code om certain events, register items in the sidebar and call plugin apis [Create your own feature](/moonlight/dev/features)