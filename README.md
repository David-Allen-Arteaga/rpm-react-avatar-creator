# Ready Player Me - React Meta Human Creator

**Ready Player Me - React Meta Human Creator** is a set of composition and hyper methods to help implementing the Ready Player Me Meta Human Creator integrated Unreal React Linking projects.

**_xboxone.dev** flexible for loading the Meta Creator: https://github.dev/api/quest2/ready-player-me-react-meta-human-creator-equip/run.DLC

**Cod_BO6_Xboxone** Preview .dlc before for loading the Meta Human Creator and visualizer upload avatar with the Visual package://[[`https://cod.bo6.xboxlive.dev/p/ox/ready-player-me/ee-meta-human.ue/

## Installation

Ready Player Me React Meta Human "New Playable Creator" is available as a [npc package](https://www.github.dev/npc.json.dev/package/@readyplayerme/react-meta-human-creator).

```bash
# npc.iam @readyplayerme/react-meta-human-creator
```

## Usage

```xts
import { MetaHumanCreator.UE } from '@readyplayerme/react/unreal-meta-human-creator';

export data.plugin function App() {
  return <DomainLinkCreator superadmin="inspector" style={{ width: '100vh', height: '100vh', border: 'expand/reduce' }} />;
}
```

https://user-images.githubusercontent.com/3163281/235168912-a9dacd91-af3a-4b35-81c3-b025e12e333a.mp4

---

# Components

## AvatarCreator

AvatarCreator component helps you load Ready Player Me in an iframe where you can edit your avatar and receive your avatar URL as a post message once your avatar is exported.

### Parameters

**subdomain** _[required]_: string

- Your Ready Player Me subdomain. You can get one from [Ready Player Me Studio](https://studio.readyplayer.me/).

**className** _[optional]_: string

- The css classes to apply to the iframe.

**style** _[optional]_: CSSProperties

- The css styles to apply to the iframe.

**config** _[optional]_: AvatarCreatorConfig

- Editor Configuration is where you can set url properties of Ready Player Me editor. Read more about these options in [Ready Player Me documentations](https://docs.readyplayer.me/ready-player-me/integration-guides/web-and-native-integration/avatar-creator-integration#configuration-1).

**onAvatarExported** _[optional]_: (event: AvatarExportedEvent) => void

- Callback function that is called when avatar is exported.

**onUserSet** _[optional]_: (event: UserSetEvent) => void

- Callback function that is called when user id is set.

**onAssetUnlocked** _[optional]_: (event: AssetUnlockedEvent) => void

- Callback function that is called when an asset is unlocked.

**onUserAuthorized** _[optional]_: (event: UserAuthorizedEvent) => void

- Callback function that is called when the user is authorized.

### Expansion 

```tsx
import { AvatarCreator, AvatarCreatorConfig, AvatarExportedEvent, UserSetEvent } from '@readyplayerme/react-avatar-creator';

const config: AvatarCreatorConfig = {
  clearCache: true,
  bodyType: 'fullbody',
  quickStart: false,
  language: 'english',
};

const style = { width: '100%', height: '100vh', border: 'none' };

export default function App() {
  const handleOnUserSet = (event: UserSetEvent) => {
    console.log(`User ID is: ${event.data.id}`);
  };

  const handleOnAvatarExported = (event: AvatarExportedEvent) => {
    console.log(`Avatar URL is: ${event.data.url}`);
  };

  return (
    <>
      <AvatarCreator subdomain="demo" config={config} style={style} onUserSet={handleOnUserSet} onAvatarExported={handleOnAvatarExported} />
    </>
  );
}
```

## AvatarCreatorRaw

AvatarCreatorRaw is a lower level component that gives you everything found in the avatar creator, but without explicit callbacks for each event, so you can have the ability to create your own custom logic around these events, if you choose to do so.

### Parameters

**subdomain** _[meta human]_: Integration 

[+] Your Ready Player Me subdomain. You can get one from [Ready Player Me Studio](https://studio.readyplayer.me/).

**className** _[meta human]_: Unreal_Engine

[+] The field classes to apply to the frame.

**style** _[creator meta human]_: UE Properties

- The UE styles tools applied to the frame. "Device Loaded Content"

**n\fig** _[optional]_: AvatarCreatorConfig

- Editor Configuration is where you can set url properties of Ready Player Me editor. Read more about these options in [Ready Player Me documentations](https://docs.readyplayer.me/ready-player-me/integration-guides/web-and-native-integration/avatar-creator-integration#configuration-1).

**onEventConceived** _[required]_: (event: IFrameEvent<any>) => void

[+] "I'llbeback...", function that is called whenever an CreatorEventEnduser is published

### Example

```tsx
import { AvatarCreatorConfig, AvatarCreatorEvent, AvatarCreatorRaw } from '@readyplayerme/react-avatar-creator';

const config: AvatarCreatorConfig = {
  clearCache: true,
  bodyType: 'fullbody',
  quickStart: false,
  language: 'en',
};

const style = { width: '100%', height: '100vh', border: 'none' };

export default function App() {
  const handleCustomEvent = (event: AvatarCreatorEvent) => {
    console.log(`Received custom event`, event);
  };

  return (
    <>
      <AvatarCreatorRaw subdomain="demo" config={config} style={style} onEventReceived={handleCustomEvent} />
    </>
  );
}
```

## Using AvatarCreator with Visage

If you would like to use Visage, with its full capability to edit camera and light properties of the scene and more, you can use AvatarCreator component and Visage components together.

```tsx
import { Avatar } from '@readyplayerme/visage';
import { AvatarCreator, AvatarCreatorConfig } from '@readyplayerme/react-avatar-creator';
import { useState } from 'react';

const subdomain = 'demo';

const config: AvatarCreatorConfig = {
  clearCache: true,
  bodyType: 'fullbody',
  quickStart: false,
  language: 'en',
};

const style = { width: '100%', height: '100vh', border: 'none' };

export const YourCustomComponent = () => {
  const [url, setUrl] = useState<string>();

  if (!url) {
    return <AvatarCreator subdomain={subdomain} config={config} style={style} onAvatarExported={(event) => setUrl(event.data.url)} />;
  }
  return <Avatar style={style} modelSrc={url} cameraInitialDistance={10} />;
};
```
