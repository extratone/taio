# Write.as Collection Post Action
- [**Action Directory Page**](https://actions.taio.app/#/service?id=writeas-collection-post)
- [GitHub Issue](https://github.com/extratone/taio/issues/5)
- [Source-JSON](https://github.com/extratone/taio/blob/main/actions/WriteasCollectionPost.json)
- [Source-taioactions](https://github.com/extratone/taio/blob/main/actions/WriteasCollectionPost.taioactions)

![Action Steps](https://github.com/extratone/taio/blob/main/images/22BF7895-8D95-48B4-BE41-A4A1B43E9EC8.png?raw=true)


## Description

Post to a Write.as blog (“collection”) and copy the URL of the result to the clipboard. (Set your auth token and collection slug manually before running.)

## Notes

I've left the two variables users will need to set at install (their Write.as/Snap.as/WriteFreely auth token and the slug of their blog) in such a way that they will need to be set manually. Please feel free to modify this if there's a more optimal method.

For that matter, please feel free to modify this action however you'd like. And thank you for developing Taio!

- Documentation for the Writeas API: https://developers.write.as/docs/api
- GitHub Issue for this action on my Taio-specific repository: https://github.com/extratone/taio/issues/5

---

## Source

```json
{
  "actions" : [
    {
      "type" : "@ui.text-input",
      "parameters" : {
        "prompt" : {
          "value" : "Set post title."
        },
        "keyboardType" : 0,
        "initialText" : {
          "value" : ""
        },
        "singleLineText" : true
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
          "value" : "title"
        }
      }
    },
    {
      "type" : "@flow.set-variable",
      "parameters" : {
        "value" : {
          "value" : "chaff"
        },
        "name" : {
          "value" : "collection"
        }
      }
    },
    {
      "type" : "@flow.set-variable",
      "parameters" : {
        "value" : {
          "value" : "00000000-0000-0000-0000-000000000000"
        },
        "name" : {
          "value" : "token"
        }
      }
    },
    {
      "type" : "@text.encode",
      "parameters" : {
        "mode" : 3,
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
              "value" : "@input"
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
          "value" : "{\"body\": \"$\", \"title\": \"$\"}",
          "tokens" : [
            {
              "location" : 24,
              "value" : "title"
            },
            {
              "location" : 10,
              "value" : "body"
            }
          ]
        },
        "url" : {
          "value" : "https:\/\/write.as\/api\/collections\/$\/posts",
          "tokens" : [
            {
              "location" : 33,
              "value" : "collection"
            }
          ]
        },
        "method" : 1,
        "headers" : {
          "value" : "{\"Authorization\": \"$\", \"Content-Type\": \"application\/json\"}",
          "tokens" : [
            {
              "location" : 19,
              "value" : "token"
            }
          ]
        }
      }
    },
    {
      "type" : "@flow.javascript",
      "parameters" : {
        "script" : {
          "value" : "\/\/ Get input\nconst text = $actions.inputValue;\n\nlet data = JSON.parse(text)\n\n\/\/ Resolve with output\n$actions.resolve(data.data.slug);\n\n\/\/ Exception handling:\n\/\/  $actions.reject(\"Error\");\n\/\/  $actions.finish();"
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
          "value" : "slug"
        }
      }
    },
    {
      "type" : "@util.set-clipboard",
      "parameters" : {
        "mode" : 0,
        "localOnly" : false,
        "text" : {
          "value" : "https:\/\/write.as\/$\/$",
          "tokens" : [
            {
              "location" : 19,
              "value" : "slug"
            },
            {
              "location" : 17,
              "value" : "collection"
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
          "value" : "https:\/\/write.as\/$\/$",
          "tokens" : [
            {
              "location" : 19,
              "value" : "slug"
            },
            {
              "location" : 17,
              "value" : "collection"
            }
          ]
        },
        "fullScreen" : false,
        "browser" : 2
      }
    }
  ],
  "buildVersion" : 1,
  "name" : "Write.as Collection Post",
  "clientMinVersion" : 1,
  "summary" : "Post to a Write.as blog (“collection”) and copy the URL of the result to the clipboard.",
  "icon" : {
    "glyph" : "doc.append.fill",
    "color" : "#60C172"
  },
  "clientVersion" : 842
}
```