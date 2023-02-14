https://sass-lang.com/documentation/

# SASS (scss) workflow.

-Er wordt geen .css meer geschreven. (in een .scss file kan je wel gewoon reguliere css syntax schrijven, maar scss support dingen als nesting.)

-Elke change in scss compiled naar een nieuwe .css file. Dus indien de site.css aangepast wordt, wordt dat bij de eerst volgende compile overscheden. Je hoeft dus in geen enkele situatie een .css file te openen/bewerken.

## Installation

Om te compilen heb je sass nodig. (of je installeert een plugin maar liever niet zodat iedereen dezelfde compile methode heeft).

```
npm install -g sass

```

Om te verifierfen op het werkt
`sass`
✅?

## Usage

Vervolgens cd directory waar de moederfile zit. cd `PimShop/wwwroot/css/scss`. Eerst de scss moederfile waar alle partials in staan gevolgd door de .css waarin je wilt compilen (site.css)`watch sass site.scss site.css`

## VSC tasks

om niet steeds dit uit te voeren kan je een task aanmaken. Inde base dir van het project maak je een nieuwe tasks.json aan in ./.vscode. Vervolgens plak je deze task erin. Zit ook een dotnet watcher voor de frontend in. Live builder zonder te debuggen.

```
{
	"tasks": [
		{
			"label": "watch",
			"command": "dotnet",
			"type": "process",
			"args": [
				"watch",
				"run",
				"${workspaceFolder}/PimShop/PimShop.csproj",
				"/property:GenerateFullPaths=true",
				"/consoleloggerparameters:NoSummary"
			],
			"problemMatcher": "$msCompile",
			"options": { "cwd": "${workspaceFolder}/PimShop/" }
		},
		{
			"label": "Watch Sass",
			"type": "shell",
			"command": "sass --watch PimShop/wwwroot/css/scss/site.scss PimShop/wwwroot/css/scss/site.css  --style=compressed",
			"problemMatcher": [],
			"group": {
				"kind": "build",
				"isDefault": true
			},
			"runOptions": {
				// "runOn": "folderOpen"
			}
		}
	]
}

```

Ctrl + Shift + P. >> run task >> aanklikken en nu moet je live kunnen compilen en auto refresh krijgen.
