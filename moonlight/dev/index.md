### Introduction

Moonlight is built in a modular and expandable way. To extend moonlight's functionalities, you have two options. MoonlightFeatures und MoonlightPlugins.

**Plugins**:
MoonlightPlugins are a minimal dll that implements interfaces provided by moonlight's and is registered through the plugin API management service. [Create your own plugin](/moonlight/dev/plugins)

**Features**
MoonlightFeatures are a dll and an optional asset folder which have access to moonlight's feature APIs, allowing you to execute code on certain events, register items in the sidebar, and call plugin APIs [Create your own feature](/moonlight/dev/features)