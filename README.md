## Twitch SvelteKit MultiMedia Viewer

This project is a SvelteKit app that displays multiple Twitch channels using a simple, non-API based approach to check whether a channel is live or offline.

### Project Goals

1. Display multiple Twitch channels using a SvelteKit app.
2. Determine if a channel is live or offline without using the Twitch API.
3. Embed Twitch channels using iframes, and display their live status.

### Components

#### ChannelsGrid

This is the main component that receives an array of Twitch channels and displays them using the `ChannelEmbed` component. It uses the `checkLive` function from `TwitchUtils.ts` to determine if the channel is live or not.

#### ChannelEmbed

This component creates and displays the Twitch player iframe and shows the `LiveStatus` component based on the `live` prop received.

#### LiveStatus

This component receives a boolean prop `live` and displays either "LIVE" or "OFFLINE" based on the value of `live`.

### Checking Channel Status without Twitch API

The project uses a simple approach to check if a Twitch channel is live or offline. Instead of using the Twitch API, it fetches the preview image of the channel from the static CDN URL: `https://static-cdn.jtvnw.net/previews-ttv/live_user_${channel}-1x1.jpg`.

If the channel is live, the status code of the fetch request will be 200, and if the channel is offline, the status code will be 404. This approach avoids the need for Twitch API access and provides a quick and straightforward way to determine the live status of a channel. I found you can pass any image size as a parameter to the URL, so I used a 1x1 image to keep the size of the request as small as possible.

### Running the Project

1. Clone the repository.
2. Run `pnpm install` to install dependencies.
3. Run `pnpm run dev` to start the development server.
4. Open `http://localhost:5173` in your browser to view the app.

Now you can enjoy watching multiple Twitch channels and easily see their live status without the need for the Twitch API!
