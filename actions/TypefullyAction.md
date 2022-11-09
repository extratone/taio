# Typefully Action
Updated `11082022-200009`

- [GitHub Issue](https://github.com/extratone/taio/issues/19)
- [Pastery](https://www.pastery.net/wgpzhv/)
- [Local](actions/Typefully.taioactions)
- [Raw Repository File](https://github.com/extratone/taio/raw/main/actions/Typefully.taioactions)

---

## Meta

### Description

Sends selected text to Typefully.com as a new thread draft. If no text is selected, the entire document or clip contents will be passed.

---

## Source

```json
{
  "actions" : [
    {
      "type" : "@editor.selected-text",
      "parameters" : {
        "fallback" : 1
      }
    },
    {
      "type" : "@text.encode",
      "parameters" : {
        "mode" : 0,
        "decode" : false,
        "text" : {
          "value" : "$",
          "tokens" : [
            {
              "location" : 0,
              "value" : "@input"
            }
          ]
        },
        "base64Options" : 0
      }
    },
    {
      "type" : "@flow.set-variable",
      "parameters" : {
        "value" : {
          "value" : "$",
          "tokens" : [
            {
              "location" : 0,
              "value" : "@input"
            }
          ]
        },
        "name" : {
          "value" : "encoded"
        }
      }
    },
    {
      "type" : "@util.open-url",
      "parameters" : {
        "url" : {
          "value" : "https:\/\/typefully.com\/?new=$",
          "tokens" : [
            {
              "location" : 27,
              "value" : "encoded"
            }
          ]
        },
        "fullScreen" : false,
        "browser" : 1
      }
    }
  ],
  "buildVersion" : 1,
  "name" : "Typefully",
  "clientMinVersion" : 1,
  "summary" : "Sends selected text to Typefully.com as a new thread draft. If no text is selected, the entire document or clip contents will be passed.",
  "icon" : {
    "glyph" : "keyboard.chevron.compact.left",
    "color" : "#3FA1F8"
  },
  "clientVersion" : 1202
}
```