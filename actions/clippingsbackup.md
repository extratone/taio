# Clippings Backup Taio Action

- [**GitHub Issue**](https://github.com/extratone/taio/issues/23)
- [URL Scheme](taio://actions?action=run&name=Clippings%20Backup) - `taio://actions?action=run&name=Clippings%20Backup`
- [Taio](taio://editor?action=open&path=%2Ftaio%2Factions%2Fclippingsbackup.md&location=2)

![Clippings Backup Action](https://cdn-images-1.medium.com/proxy/1*7Fhwhl3sjH_ZuLxJig9hBQ.png)

## Metadata

### Action Description

Backs up all clippings content - merged in a single text file - at [iCloud Storage]/clippings.md.

### Description

This action uses the [Get Clippings action step](https://docs.taio.app/#/integration/shortcuts?id=get-clippings) to return the content of all clippings, which is then counted by lines and backed up (by default) in the root of one's iCloud Drive storage for Taio as `clippings.md`. (`iCloud Drive/Taio/Editor/clippings.md`) Before finishing, the actions displays the number of lines it has backed up.

## Video Demo

<video controls width="480" height=auto>
  <source src="https://github.com/extratone/taio/assets/43663476/6e2887d8-fb89-4683-8ecc-c9cfd6bb02c1">
</video>

---

## Source

- [GitHub](https://github.com/extratone/taio/blob/main/actions/ClippingsBackup.taioactions)
- [Pastery](https://www.pastery.net/geunbs)

<script>(function(d, s, id) {var js, pastejs = d.getElementsByTagName(s)[0];if (d.getElementById(id)) return;js = d.createElement(s); js.id = id;js.src ='https://www.pastery.net/static/js/embed.js';pastejs.parentNode.insertBefore(js, pastejs);}(document, 'script', 'pastery-jssdk'));</script><div class='paste-list' data-pasteid='geunbs'></div>

```json
{
	"actions": [
		{
			"type": "@clips.get-text",
			"parameters": {
				"mode": 1
			}
		},
		{
			"type": "@flow.set-variable",
			"parameters": {
				"value": {
					"value": "$",
					"tokens": [
						{
							"location": 0,
							"value": "@input"
						}
					]
				},
				"name": {
					"value": "clippings"
				}
			}
		},
		{
			"type": "@text.count",
			"parameters": {
				"mode": 0,
				"text": {
					"value": "$",
					"tokens": [
						{
							"location": 0,
							"value": "clippings"
						}
					]
				}
			}
		},
		{
			"type": "@flow.set-variable",
			"parameters": {
				"value": {
					"value": "$",
					"tokens": [
						{
							"location": 0,
							"value": "@input"
						}
					]
				},
				"name": {
					"value": "count"
				}
			}
		},
		{
			"type": "@editor.new",
			"parameters": {
				"location": 2,
				"openInEditor": false,
				"filename": {
					"value": "clippings.md"
				},
				"text": {
					"value": "$",
					"tokens": [
						{
							"location": 0,
							"value": "clippings"
						}
					]
				},
				"overwriteIfExists": true
			}
		},
		{
			"type": "@ui.toast",
			"parameters": {
				"style": 0,
				"waitUntilDone": false,
				"title": {
					"value": "$ Clippings Backed Up",
					"tokens": [
						{
							"location": 0,
							"value": "count"
						}
					]
				}
			}
		}
	],
	"buildVersion": 1,
	"name": "Clippings Backup",
	"clientMinVersion": 1,
	"summary": "Backs up all clippings content - merged in a single text file - at [iCloud Storage]/clippings.md.",
	"icon": {
		"glyph": "externaldrive.badge.checkmark",
		"color": "#10ADC0"
	},
	"clientVersion": 1222
}
```