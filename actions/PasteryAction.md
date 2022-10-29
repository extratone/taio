# Pastery Taio Action
Updated `10122022-091754`

- [**Action File**](https://davidblue.wtf/taio/Pastery.taioactions)
- [GitHub Issue](https://github.com/extratone/taio/issues/18)
- [**Paste**](https://www.pastery.net/zhnzzj)
- [JSON Paste](https://www.pastery.net/kpebej)
- [Repository Action File](https://github.com/extratone/taio/blob/main/actions/Pastery.taioactions)
- [Taio](taio://editor?action=open&path=%2Ftaio%2Factions%2FPasteryAction.md&location=2)
- [WTF](https://davidblue.wtf/drafts/54B114CA-AEB5-403F-AB95-790D3FBA627B.html)
- [WTF Shortlink](https://davidblue.wtf/taio/pastery) - `https://davidblue.wtf/taio/pastery`
- [Local](shareddocuments:///private/var/mobile/Library/Mobile%20Documents/com~apple~CloudDocs/Written/54B114CA-AEB5-403F-AB95-790D3FBA627B.md)
- [Video Demo](https://user-images.githubusercontent.com/43663476/195356023-5872afa1-23fb-4fdd-bcb5-2e424ca78a16.MOV)
- [Ulysses](ulysses://x-callback-url/open?id=JnsXlcgiq8J97jPRnoQf6A)
- [Medium](https://extratone.medium.com/pastery-taio-action-4b52a7e4f3a6)
- [Things](things:///show?id=6PiEEqfMAmgXButT4g7JeM)

---

## Social

<script async="" src="https://telegram.org/js/telegram-widget.js?1" data-telegram-post="extratone/12968" data-width="100%"></script>

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">Another simple API action for <a href="https://twitter.com/TaioApp?ref_src=twsrc%5Etfw">@TaioApp</a>... This time, for *the greatest pastebin in the world*. <a href="https://t.co/N0BGTt8p8L">https://t.co/N0BGTt8p8L</a> <a href="https://t.co/lawmfTWALo">pic.twitter.com/lawmfTWALo</a></p>&mdash; 𝗗 𝗔 𝗩 𝗢 𝗗 (@NeoYokel) <a href="https://twitter.com/NeoYokel/status/1580198141357342722?ref_src=twsrc%5Etfw">October 12, 2022</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

Another simple API action for @TaioApp... This time, for *the greatest pastebin in the world*. https://davidblue.wtf/taio/pastery

- [Twitter](https://twitter.com/NeoYokel/status/1580198141357342722)
- [Telegram](https://t.me/extratone/12968)

---

[![Pastery Taio Action](https://github.com/extratone/taio/blob/main/images/C59CE448-4075-4711-AC54-C98A7EF5CE54.png?raw=true)](https://davidblue.wtf/drafts/54B114CA-AEB5-403F-AB95-790D3FBA627B.html)

<script>(function(d, s, id) {var js, pastejs = d.getElementsByTagName(s)[0];if (d.getElementById(id)) return;js = d.createElement(s); js.id = id;js.src ='https://www.pastery.net/static/js/embed.js';pastejs.parentNode.insertBefore(js, pastejs);}(document, 'script', 'pastery-jssdk'));</script><div class='paste-list' data-pasteid='zhnzzj'></div>

## Submission

- [Airtable Automated Response](message:%3C20221029114010.219e9cb19df74f19@airtable.com%3E)

## Description

Create a Pastery paste via API with the current document's contents. The result's URL will be passed to the system clipboard.

You'll need to change the value of the `apikey` variable to your own Pastery API key.

See Pastery's API documentation: https://www.pastery.net/api

## Directory Description

Create a Pastery paste via API with the current document's contents. At run, you'll be prompted to set the `duration` parameter of the call in minutes. The default value (`10512000`) equates to 20 years. You'll also be prompted to select a syntax highlighting language from [Pastery's official supported list](clippings/pasterylang.md). The result's URL will be passed to the system clipboard.

**Please note**: Before running this action, you'll need to change the value of the `apikey` variable to your own Pastery API key.

*See [Pastery's API documentation](https://www.pastery.net/api)*

## Video Demo

<video controls width="520" height=auto>
  <source src="video/PasteryActionDemo.MP4">
</video>

- [Raw File](video/PasteryActionDemo.MP4)
- [Twitter Media Studio](https://studio.twitter.com/library/13_1580195391965904899)
- [YouTube](https://youtu.be/5GBe2jL5PEI)

## JSON

<script>(function(d, s, id) {var js, pastejs = d.getElementsByTagName(s)[0];if (d.getElementById(id)) return;js = d.createElement(s); js.id = id;js.src ='https://www.pastery.net/static/js/embed.js';pastejs.parentNode.insertBefore(js, pastejs);}(document, 'script', 'pastery-jssdk'));</script><div class='paste-list' data-pasteid='kpebej'></div>

```json
{
  "actions" : [
    {
      "type" : "@flow.set-variable",
      "parameters" : {
        "value" : {
          "value" : "YOURAPIKEY"
        },
        "name" : {
          "value" : "apikey"
        }
      }
    },
    {
      "type" : "@editor.filename",
      "parameters" : {
        "mode" : 0,
        "includeExtension" : false
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
          "value" : "filename"
        }
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
              "value" : "@editor.full-text"
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
              "value" : "@editor.full-text"
            }
          ]
        },
        "name" : {
          "value" : "body"
        }
      }
    },
    {
      "type" : "@util.request",
      "parameters" : {
        "body" : {
          "value" : "$",
          "tokens" : [
            {
              "location" : 0,
              "value" : "body"
            }
          ]
        },
        "url" : {
          "value" : "https:\/\/www.pastery.net\/api\/paste\/?title=$&api_key=$&language=markdown",
          "tokens" : [
            {
              "location" : 51,
              "value" : "apikey"
            },
            {
              "location" : 41,
              "value" : "filename"
            }
          ]
        },
        "method" : 1,
        "headers" : {
          "value" : "{\"Content-Type\": \"text\/plain\"}"
        }
      }
    },
    {
      "type" : "@flow.javascript",
      "parameters" : {
        "script" : {
          "value" : "\/\/ Get input\nconst text = $actions.inputValue;\n\nlet data = JSON.parse(text)\n\n\/\/ Resolve with output\n$actions.resolve(data.url);\n\n\/\/ Exception handling:\n\/\/  $actions.reject(\"Error\");\n\/\/  $actions.finish();"
        }
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
          "value" : "url"
        }
      }
    },
    {
      "type" : "@ui.toast",
      "parameters" : {
        "style" : 1,
        "waitUntilDone" : true,
        "title" : {
          "value" : "Paste created - URL passed to system clipboard"
        }
      }
    },
    {
      "type" : "@util.set-clipboard",
      "parameters" : {
        "mode" : 0,
        "localOnly" : false,
        "text" : {
          "value" : "$",
          "tokens" : [
            {
              "location" : 0,
              "value" : "url"
            }
          ]
        },
        "expireAfter" : {
          "value" : "0"
        }
      }
    },
    {
      "type" : "@util.open-url",
      "parameters" : {
        "url" : {
          "value" : "$",
          "tokens" : [
            {
              "location" : 0,
              "value" : "url"
            }
          ]
        },
        "fullScreen" : false,
        "browser" : 2
      }
    }
  ],
  "buildVersion" : 1,
  "name" : "Pastery",
  "clientMinVersion" : 1,
  "summary" : "Create a Pastery paste via API with the current document's contents. The result's URL will be passed to the system clipboard.\n\nYou'll need to change the value of the `apikey` variable to your own Pastery API key.\n\nSee Pastery's API documentation: https:\/\/www.pastery.net\/api",
  "icon" : {
    "glyph" : "arrow.triangle.2.circlepath.doc.on.clipboard",
    "color" : "#FB6666"
  },
  "clientVersion" : 842
}
```