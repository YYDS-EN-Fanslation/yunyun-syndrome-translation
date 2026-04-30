# Yunyun Syndrome Translation files

These are translation files for game [Yunyun Syndrome!? Rhythm Psychosis](https://store.steampowered.com/app/2914150/Yunyun_Syndrome_Rhythm_Psychosis/)
from [YYDS EN Fanslation Project](https://github.com/YYDS-EN-Fanslation). These are just .csv patches intended for developers/translators, in order to apply them
to the game you need to use either [patcher](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-patch) or [mod](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-mod).

The files were exported from [YYDS EN Fanslation Google Sheets](https://docs.google.com/spreadsheets/d/1WfkeD6KFqCWBM-JGu3l_6HwCyER5Z5BzFZgZ8IDL9L0/edit?gid=551366469#gid=551366469&fvid=2041749061).  
You can also use [mod](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-translation) to dump all the translation strings to [make your own patches](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-mod#how-to-make-patches).

Looking for something else?
- [Yunyun Syndrome Patch](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-patch) - Translation patcher with simple installer
- [Yunyun Syndrome Mod](https://github.com/YYDS-EN-Fanslation/yunyun-syndrome-mod) - Melonloader translation mod
- [YYDS EN Fanslation Project](https://github.com/YYDS-EN-Fanslation) - More information about YYDS EN Fanslation Project
- [YYDS EN Fanslation Discord](https://discord.com/invite/Pd3CWA8BfD) - Our Discord

## Format

Both patcher and mod use same 3-column CSV format([RFC 4180](https://www.rfc-editor.org/rfc/rfc4180.html)). The columns are as follow:
`TableName`, `Key`, `Text`. Yunyun Denpa Syndrome stores translations strings in 2 ways. Unity Localization's StringTables and `.lang` TextAssets.

### UnityEngine.Localization.Tables.StringTable

This is a standard way of providing localization in Unity. Each locale provides set of StringTables which are then dynamically loaded on demand during gameplay.
For these strings, `tableName` corresponds to StringTable's name(`Object.name` not `LocalizationTable.TableCollectionName`), `Key` to `TableEntry.Key`
and `Value` to `TableEntry.LocalizedValue`.

For example:
```csv
TableName,Key,Text
Text_en,UITitle/Load,LOAD DREAM
```

### .lang JSON TextAssets

These files are used by game's propietary VN/scene engine. They consists of JSON TextAssets which hold lines of texts for each supported language.
The basic schema is like this:

```ts
{
    "Keys": string[],
    "List": Array<{
        "Default": boolean,
        "Language": string,
        "Lines": string[]
    }>
}
```

For these strings, `tableName` corresponds to TextAsset's name, `Key` to `<language>/<line_no>` and `Value` to new text.

For example:
```csv
TableName,Key,Text
YUNYUN_001_Main_000_000.lang,en/0,"Hello Yunyun here, yun!"
```
