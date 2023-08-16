---
title: [YouTube Data]
type: checkup
---
# YouTube 

This is a walkthrough to downloading your YouTube watch history. 

## Downloading Data

{{< code-action "Follow along with this video and the steps below to download your YouTube watch history." >}} 

<br>
<br>


{{< youtube "eq1SKWlidJ4" >}}

> 0. **Go to [Google Takeout](https://takeout.google.com/settings/takeout).** Make sure you are logged into the Google account you would like to download your Youtube data from. 
> 0. **Select `Deselect all`.** This will ensure you only download your Youtube data, as opposed to all of the data Google assosicates with your account.
> 0. **Scroll to the bottom and find `YouTube and YouTube Music` and check the box.** 
> 0. **Select `Multiple Formats`.** 
>       -  **For `History`, select `HTML` and choose `JSON`. Then, click `OK`.**
> 0. **Select `All Youtube data included`**
>       - **Select `Deselect all`**
>       - **Select `history`**
>       - **Select `OK`**
> 0. **Select `Next step`**
> 0. **Scroll down, select `Create export`.**
> 
> This may take awhile. It may only take a few minutes or an hour. You will receive an email when your data is ready for download.


{{< code-action "Once your data is ready to download, you'll need to locate the correct file.." >}} 

{{< figure src="images/courses/cs9/unit01/youtube_download.gif" width="100%" >}}
> 0. **Download the first export.** You do not need to download all of the exports. 
> 0. **Open the `.zip` file.**
> 0. **Navigate to the `Takeout 6/YouTube and YouTube Music/history` folder.**
> 0. **Move the `watch_history.json` into your `desktop/cs9/unit_01` folder.**

---

## API Key


{{< code-action "Follow along with this video to get a YouTube API key." >}} You will need this to build out your data file with statistical information. 


{{< youtube "5Ym13tgVtAw" >}}

> 0. **Go to the [Google Cloud Platform Library](https://console.cloud.google.com/projectselector2/apis/library?organizationId=1025210370450&supportedpurview=project).** 
> 0. **Select `isf.edu.hk` on the top toolbar on the lefthand side.** 
> 0. **Change `Project name` to 'cs9 data science'.** 
> 0. **Select `CREATE`.** This may take a full minute. 
> 0. **Search for `youtube data v3`.** Select it from the search results. 
> 0. **Select `ENABLE`.** This may take a full minute.
> 0. **Select `Credentials` from the left menu.**
> 0. **Select `CREATE CREDENTIALS` from the top menu.**
> 0. **Select `API key` from the dropdown menu.**
> 0. **Copy and paste your `API key` to somewhere you will not lose it..**
>
> If you forget your API key, return to [this](https://console.cloud.google.com/apis/credentials) page to access it.

