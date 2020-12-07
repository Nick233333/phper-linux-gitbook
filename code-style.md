Git 提交 PHP 代码风格检测配置

```json
{
	"require": {
		"friendsofphp/php-cs-fixer": "^2.16",
		"brainmaestro/composer-git-hooks": "^2.8"
	},
	"extra": {
		"hooks": {
			"pre-commit": [
				"composer check-style"
			],
			"post-merge": "composer install"
		}
	},
	"scripts": {
		"post-update-cmd": [
			"cghooks update"
		],
		"post-install-cmd": [
			"cghooks add --ignore-lock",
			"cghooks update"
		],
		"cghooks": "vendor/bin/cghooks",
		"check-style": "php-cs-fixer fix --using-cache=no --diff --config=.php_cs --dry-run --ansi",
		"fix-style": "php-cs-fixer fix --using-cache=no --config=.php_cs --ansi"
	},
	"scripts-descriptions": {
		"check-style": "Run style checks (only dry run - no fixing!).",
		"fix-style": "Run style checks and fix violations."
	}
}

```