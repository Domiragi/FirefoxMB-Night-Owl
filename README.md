<h2 align="center"><a href="#wrench-installation"><img src="https://user-images.githubusercontent.com/61329159/204102654-0e414196-bea2-4147-9e1e-aeb8b4190893.png" width="20" height="20" /></a> Firefox Mod Blur - Night Owl</h2>

<p align="center">
<a href="#version_badge"><img alt="Version" src="https://img.shields.io/badge/Last%20tested%20Firefox-v145.x-blue?style=flat&logo=firefox&logoColor=white"></a>
</p>

<p align="center">
  <img alt="Light" src="https://github.com/user-attachments/assets/ef4de394-7fe0-4aee-b852-87d9a59cc70d" width="48%">
&nbsp;
  <img alt="Dark" src="https://github.com/user-attachments/assets/8335fdf5-8949-4536-a566-a44f6875d513" width="48%">
</p>

<p align="center">
  <img src="https://github.com/user-attachments/assets/d82013ad-e813-4f6f-9080-4cb5d1829d73" alt="Night Owl Demo" width="85%"/>
</p>

<div style="text-align: justify">
	
# Description
	
This is a personalized fork of Firefox Mod-Blur, and my take on the [VSCode Night Owl theme](https://vscodethemes.com/e/sdras.night-owl/night-owl).

The project uses Firefox Mod-Blur as the base structure, and have been modified (thanks to the codes from [uc.css.js](https://github.com/aminomancer/uc.css.js)) to extend its customization capabilities to many parts of the internal system. Although the color scheme takes inspiration from the Night Owl theme, I only use a selected number of main colors that I like from Night Owl for this project to create a more coherent look.

<details>
<summary>About the extra `userChrome.css` and `userContent.css` files</summary>

The main files for customizing Firefox are `userChrome.css` and `userContent.css`, but you'll see that there are also `userChrome_main.css`, `userChrome_sub.css`, `userContent_main.css`, `userContent_sub.css`. The reason for this is that in the upstream repo, all of the main config codes are written directly in the `userChrome.css` and `userContent.css` files; this makes it really hard to add your own customization because all the custom files are imported at the head of the file, so if you want to make a change you'll to directly modify the content of the file, and that makes it hard to merge changes from upstream if you change it extensively. So I break `userChrome.css` into `userChrome_main.css` and `userChrome_sub.css` where `userChrome_sub.css` contains everything from `userChrome.css` without importing any extra files; that instead is done in `userChrome_main.css` where it imports `userChrome_sub.css` as the first file, then imports all the extra custom files. That way, all the custom changes can be written in the custom files that come after and it will overwrite the codes in the original files without having to directly modify it, and the original `userChrome.css` can be kept to pull changes from upstream. The same is applied to `userContent.css`. Until the upstream repo changes its approach to file structure, I think this is the best way to go about it.

The only main config files you need are `userChrome_main.css`, `userChrome_sub.css`, `userContent_main.css`, `userContent_sub.css`; once you copy these files to your `chrome` folder, `userChrome_main.css` and `userContent_main.css` should be renamed to `userChrome.css` and `userContent.css`.

</details>

95% of the customizing comes from the CSS files, the rest are from the use of JavaScript to further extend the capability, most notably the custom [Findbar from uc.css.js](https://github.com/aminomancer/uc.css.js/blob/master/JS/findbarMods.uc.js). Using JavaScript files is totally optional.

As mentioned this is a personalized fork, so although much of the codes from Firefox Mod-Blur is the same, I changed and removed many things that I don't use to keep the code streamlined for me, most significantly the support for vertical tabbar, and several other mods. I advise you to check the original Firefox Mod-Blur to see its full capability, and check the commit history of this project to see exactly what was changed/removed.

Many thanks to [Firefox-Mod-Blur](https://github.com/datguypiko/Firefox-Mod-Blur), on which this entire project is based on, and many thanks to [uc.css.js](https://github.com/aminomancer/uc.css.js) for being a great source of information on how to config the internal system of Firefox. I also want to note [FF-ULTIMA](https://github.com/soulhotel/FF-ULTIMA), a really cool looking project and helped me with minor tweaks here and there.

# Usage/Installation
If you are unfamiliar with customizing Firefox, I strongly advise you to look up what `userChrome.css`, `userContent.css` and `user.js` files are and what they do. https://www.userchrome.org/ is a good resource for that.

## Installation Steps
1. Enable Firefox to use customization files: Either copy my `user.js` file into your Profile folder, or enable it through `about:config`
  * ***Option A.*** Copy `user.js`, if you also want to use my settings:
    1. Enter `about:profiles` into your URL/searchbar. Locate the profile you are currently using, which will most likely be named `default` or `default-release`. The correct one won't have the `Set as default profile` button.
    2. In the row for Root Directory, press the `Open Folder` button. It will bring up the folder for your profile, copy and paste the `user.js` file into that folder. Restart Firefox and run once to copy the changes from `user.js` to `pref.js`, then you can delete the `user.js` file.
  * ***Option B.*** Change through `about:config`: Enter `about:config` into your URL/searchbar, then search for `toolkit.legacyUserProfileCustomizations.stylesheets` and set it to `true`.
2. Copy the customization files: Follow the steps in Step 1 with `user.js` to locate to your Profile folder. In your Profile folder, create a new folder named `chrome`. In the new `chrome` folder, copy and paste there the files `userChrome_main.css`, `userChrome_sub.css`, `userContent_main.css`, `userContent_sub.css`, as well as the folder `ASSETS`.
3. Rename the files `userChrome_main.css` and `userContent_main.css` to `userChrome.css` and `userContent.css`.
4. Using extra mods: Copy the `.css` files from the folders of the mods you want to use into the `chrome` folder. Some mods have specific instructions, so make sure to check the `README` files in those folder before use. The `userChrome_main.css` only imports the extra mods that I currently use, so you'll want to modify it for your personal use.
5. To use JavaScript files, check the [README file](https://github.com/Domiragi/FFox-MB/tree/custom/EXTRA%20MODS/JavaScript) in the JavaScript folder.
6. To use the Night Owl theme, copy the `.css` files from the Night-Owl folder into your `chrome` folder.

# Extra Resources
- https://www.userchrome.org/ : A good resource on `userChrome.css` and configuring Firefox.
- https://firefox-source-docs.mozilla.org/devtools-user/browser_toolbox/ : Guide to enable the Browser Toolbox in Firefox and also disable Popup Autohide so you can inspect elements of the Firefox browser itself.
- https://firefoxcss-store.github.io/ : A collection of builds and configs from the Firefoxcss community on [Reddit](https://www.reddit.com/r/FirefoxCSS/) and on [Lemmy](https://lemmy.world/c/FirefoxCSS@fedia.io).
- https://github.com/aminomancer/uc.css.js/ : Many good codes/information on configuring the internal Firefox system. The owner/maintainer is a developer from Firefox, and many of [his comments in r/Firefoxcss](https://www.reddit.com/r/FirefoxCSS/search/?q=MotherStylus) have been extremely informative.
- The owl icon is from [G-CAT](https://www.flaticon.com/free-icon/owl_13037142)
- The font is CommitMono Nerd Font: https://www.nerdfonts.com/font-downloads

<details>
<summary><h2>TODO </h2></summary>
	
- [ ] Fix the `Audio Icon In Top Right` mod that was broken after v.136
- [ ] Config the Autoscroll Icon

</details>

</div>
