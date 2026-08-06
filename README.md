# 🌍 easyDialog
This is the modified easyDialog with some perks and new protections. An original modification by Awsomedude.
Idea taken from [Awsomedude/easyDialog](https://github.com/Awsomedude/easyDialog), I just made other modifications and new additions.

# 📁 Dependencies
- [Library YSI](https://github.com/pawn-lang/YSI-Includes)

# 🫧 Protections
- Protects input against malicious characters.
- Protects the dialog response entirely on the server side.
- Protects against invalid listitem responses from the client.
- Protects the player from using a hidden dialog.

# ⚠️ Notes
- You can create custom callbacks for your dialogs, see the example below.
```pawn
Dialog:CUSTOM_DIALOG(playerid, response, listitem, inputtext[]) {

    your code
    return true;
}

Dialog_Show(playerid, CUSTOM_DIALOG, style, "title", "infos", "Confirm", "Cancel");
```
- You can also redisplay the dialog with an error message, see the example below
- This ReShow function will keep the old information and add an error message to the end of the dialog with your custom message.
```pawn
Dialog:CUSTOM_DIALOG(playerid, response, listitem, inputtext[]) {

    if(response) {

        if(!strlen(inputtext))
            return Dialog_ReShow(playerid, "You need to put some information");

    }
    return true;
}

Dialog_Show(playerid, CUSTOM_DIALOG, DIALOG_STYLE_PASSWORD, "Password", "Your password", "Login", "Cancel");
```

# 📝 Functions
- Dialog_Create(playerid, const callback[], DIALOG_STYLE:style, const title[], body[], const button1[], const button2[], {Float, _}:...);
- Dialog_Show(playerid, const callback[], DIALOG_STYLE:style, const title[], body[], const button1[], const button2[], {Float, _}:...);     // Same Dialog_Open
- Dialog_Close(playerid);
- Dialog_ReShow(playerid, const error[] = "");     // Reopen the same dialog with additional message or not
- bool:Dialog_Created(playerid);

# 👋🏼 Credits
Even though I wrote the code completely, the initial idea is entirely Awsomedude, I just made the system more "gourmet" and added new protections.
You can build on the project by porting it to open-mp, I'd love to see your contribution.
