# Architecture Decision Record: Development framework
This is the architecture decision record for the beatflow app developed for CPRG303.

## Development Framework
### Summary
#### Issue 
We want to use a development framework that:
- We are familiar with
- Enables cross-platform functionality later down the line
- Has an active community that provides numerous resources to speed up development

#### Decision 
Decided on React Native as the development framework.

#### Status
Decided on React Native. 

### Details
#### Assumptions 
We believe that React Native is the best development platform for us because:
- It is cross-platform which would make it easy to develop an iOS app for later on
- It is free for us to use
- Has a robust community that provides valuable tools to aid in development and can be contacted if needed
- We would be able to get in-person support with issues that arise since our instructor specializes in this framework

#### Constraints 
If we choose a framework that outside of React Native, we would have to learn a new framework which would halt our progress heavily.

If we choose React Native we may be limited in our access to Spotify and may have to focus the app's functionality on local storage.

#### Positions
We considered React Native to be our best option because it provided us with the most support during the development of our app. With
React Native we would have access to various libraries, tools, and resources to speed up development and resolve issues. It is also the 
development framework that the team is most comfortable with and already has experience using. Going to another framework would not 
make sense for the development timeline of the app.

#### Argument
As above.

Specifically, the team's familiarity with React Native as well as access to in-person support via our instructor.

#### Implications
If there was a development framework that offered more than React Native in these aspects, then we would be 
open to building with that framework.


## Navigation Strategy
### Summary
#### Issue 
We want to use a navigation strategy that: 
- Is familiar to users who already use music apps like Spotify, Apple Music, or Youtube Music.
- Concentrates the primary navigation to the bottom of the screen
- Creates a minimal design

#### Decision 
Decided on tab navigation.

#### Status 
Decided on tab navigation. Open to a more flexible navigation stratgey.

### Details
#### Assumptions 
With a tab navigation strategy: 
- We can keep the UI minimal while providing the user with the ability to easily navigate throughout
- We can create a user-friendly UI
- We will be restricted to 4-5 main options 

#### Constraints 
If we go with tab navigation, our ability to make a clean an minimal design will be limited by the tab navigation bar's
occupation of screen space. 

If we go with tab navigation, we will be restricted to 4-5 main options for navigation.

#### Positions
We considered using drawer navigation similar to Twitter since it occupies the least amount of screen space while idle. It offers one of the 
most minimal design layouts possible for navigation. However, the drawer's design does not adhere to the style of the most 
popular music apps. This makes it less intuitive for the user.

We considered tab navigation to be the best option because we are able to keep our UI clean and minimal, while maintaining a similar style to the 
top music apps. The tab design concentrates the primary navigation to the bottom of the screen instead of hiding it away, making it familiar 
to users of other music apps and intuitive for brand new users. 
```jsx
<Tabs
    screenOptions={
      {
        headerShown: false,
        tabBarActiveTintColor: '#007bff',
        tabBarStyle: {
          backgroundColor: '#f0f0f0',
          borderTopColor: 'gray',
          borderTopWidth: 1,
          height: 60,
        },
      }}>
      <Tabs.Screen name="index" 
      options={{
        title: 'Home',
        // tabBarIcon: () => <AntDesign name="antdesign" size={28} color="black" />, @ constants/Color.ts
        // reuse size and color:
        tabBarIcon: ({color, size}) => <AntDesign name="antdesign" size={size} color={color} />,
      }}/>
      <Tabs.Screen name="contact" 
      options={{
        title: 'Contact',
        tabBarIcon: ({color, size}) => <AntDesign name="contacts" size={size} color={color}/>,
      }}/>
      <Tabs.Screen name="about" 
      options={{
        title: 'About',
        tabBarIcon: ({color, size}) => <AntDesign name="infocirlceo" size={size} color={color} />,
      }}/>
</Tabs>
```
The tab navigation is also highly customizable so we will have more control over the overall size of the navigation bar. This will
provide the ability to style it in a way that ensures we maintain a minimal design. 

#### Argument
As above.

Specifically, that the tab navigation will adhere to the current design standard for music applications, making it the best 
option for user-friendliness. 

#### Implications
If it is possible to incorporate the drawer navigation for more obscure things like "settings", then we will look
to use the drawer navigation in the app as well. 


## Hardware
### Summary
#### Issue 
We need to access hardware that will:
- Enable the correct volume controls
- Output sounds
- Enable the transference of audio to bluetooth devices

#### Decision 
Decided on speaker internal/external, bluetooth and external volume buttons.

#### Status 
Decided on speaker internal/external, bluetooth and external volume buttons. Open to the fingerprint scanner as well for quick sign-in if possible. 

### Details
#### Assumptions 
With access to the phone's speaker, bluetooth and external volume buttons:
- We will be able to give more options to the user on how they are able to consume media through our app
- Even though other devices have volume control, it is still common to change the volume setting through the phone’s volume control for most users


#### Constraints 
If the user has a bluetooth connection or a seperate speaker (through auxillary), we might have to focus the output there automatically.
- We need direct access to bluetooth to enable the ability to quickly pair a bluetooth audio device or swap between bluetooth audio devices
- We need direct access to the external volume buttons so the app can correctly respond to volume controls
- We need to make sure it prioritizes the bluetooth or external devices when and if it is connected

#### Positions
We considered the phone's speaker, bluetooth and external volume buttons as the primary hardware requirements do to their direct impact
on the user's experience. Audio output and control of that output will be a core piece of our app so we need to be able to have full 
access to the hardware that handles those aspects. We would need the ability to control which audio output is changed within the app to
ensure that the volume for the primary speaker is increased or decreased; instead of the earpiece speaker. 

#### Argument
As above.

#### Implications
We may require additional hardware to enable features.


## Database Storage
### Summary
#### Issue 
We need to use database storage that achieves:
- Data privacy
- Offline Access

#### Decision 
Decided on local encrypted storage. 

#### Status 
Decided on local encrypted storage but are persuing the ability to play songs via Spotify. 

### Details
#### Assumptions 
With local encrypted storage we will be able to: 
- Ensure data privacy and security
- Enable offline access for song playback

#### Constraints 
If we choose local encrypted storage, we will be limited to the device's storage capacity. 

#### Positions
We considered a remote database through a Spotify API connection, but it seems that we may have limitations on our ability to play music directly in the app. The Spotify APK seemed to be the best bet for song playback, however, we would have to develop the app outside of React Native if we decided to go with that option. 

We considered local encrypted storage as the best option because it provides enhanced security for sensitive data, is useful for offline functionality and simplifies the development of our app.

#### Argument


#### Implications


