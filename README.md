# Mac Karabiner Chinese Punctuations to Halfwidth Forms

When using Chinese in markdown and code, to speed the format switch of the halfwidth/fullwidth input, we can map each inputting punctuation to its halfwidth form by pressing function key `fn`.

当在markdown或者code中运用中文时，为了更快地转换半角/全角（港台：半形/全形）的符号输入，我们可以通过同时按着`fn`键把对应正在输入的符号变为半角形式。

*Note:* If you are a user of other fullwidth langauges (Japanese, Korean, etc.), you may need to modify both the `json` and `shell script` files for your need.

---

## List of All Mapped Keys（映射的个键列表）:

`fn` key + 

- `，` -> `,`
- `。` -> `.`
- `；` -> `;`
- `：` -> `:`
- `‘` -> `'`
- `“` -> `"`
- `”` -> `"`
- `·` -> `` ` ``
- `～` -> `~`
- `！` -> `!` 
- `？` -> `?`
- `（` -> `(`
- `）` -> `)`
- `【` -> `[`
- `】` -> `]`
- `「` -> `{`
- `」` -> `}`
- `《` -> `<`
- `》` -> `>`
- `¥` -> `$` 
- `……` -> `^`
- `——` -> `_`
- `、` -> `\`
- `｜` -> `|`

*Note:* in the case of the multi-key values, we should press *all* the usual keys plus the `fn` key. For instance, when mapping `……` to `^`, we should press  `shift` + `fn` + `6`.

---

## Prerequisite（所需软件）: Karabiner

![karabiner-elements-logo](https://static.macupdate.com/products/25141/m/karabiner-elements-logo.png?v=1593415409)

**Download Link:** <https://pqrs.org/osx/karabiner/>

## Installation（安裝）:

Steps:

1. Download them as zip file and then decompress [1]
2. Copy `fn_halfwidth.json` file to **~/.config/karabiner/assets/complex_modifications**
3. Copy `halfwidth_convert` file to **~/.config/karabiner/assets/complex_modifications/helpers** [2]
4. Enable rule in the complex modifictaions tag in Karabiner, see the [guide](https://karabiner-elements.pqrs.org/docs/manual/configuration/configure-complex-modifications/)

[1] It's recommended that you doanwload as zip file to preserve the permission, otherwise you may need to `chmod ug+x ~/.config/karabiner/assets/complex_modifications/helpers/halfwidth_convert` in terminal to activate the shell script for the first time use

[2] you may need to create the `helpers` folder at first

---

## Limitations

Since we use the `ruler pboard` here, sometimes the pastied characters come in a weird way in some special environments (I haven't figured out the mechanism yet). 

You may delete all the lines 

```
,{
  "shell_command": "pbpaste -pboard ruler | pbcopy" 
}
```

in the `json` file to avoid this limitation, at the cost of messing up your `general pboard`.

I will fix this bug in the future once I have time.

## Why don't we use text-replacement functions? 

There are lots of fancy text-replacement tools such as MacOS bulit-in keyboard text-replacement and Alfred 4 script.

However, for the markdown and coding scenes of fullwidth langauges, the just-in-time (JIT) halfwidth conversion is more efficient and intuitive. By using Karabiner, we can type the halfwidth punctuations just by holding a hotkey and then it would switch back to fullwidth input automatically and immediately, instead of typing a verbose replacement string each time.
