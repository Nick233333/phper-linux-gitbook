Git 提交 PHP 代码风格检测配置

`composer.json` 文件

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

`.php_cs` 文件

```php
<?php

return PhpCsFixer\Config::create()
    ->setRules([
        '@PSR2' => true,
        'binary_operator_spaces' => true,
        'blank_line_after_opening_tag' => true,
        'compact_nullable_typehint' => true,
        'declare_equal_normalize' => true,
        'lowercase_cast' => true,
        'lowercase_static_reference' => true,
        'new_with_braces' => true,
        'no_blank_lines_after_class_opening' => true,
        'no_leading_import_slash' => true,
        'no_whitespace_in_blank_line' => true,
        'ordered_class_elements' => [
            'order' => [
                'use_trait',
            ],
        ],
        'ordered_imports' => [
            'imports_order' => [
                'class',
                'function',
                'const',
            ],
            'sort_algorithm' => 'none',
        ],
        'return_type_declaration' => true,
        'short_scalar_cast' => true,
        'single_blank_line_before_namespace' => true,
        'single_trait_insert_per_statement' => true,
        'ternary_operator_spaces' => true,
        'unary_operator_spaces' => true,
        'visibility_required' => [
            'elements' => [
                'const',
                'method',
                'property',
            ],
        ],
    ])
    ->setFinder(
        PhpCsFixer\Finder::create()
            ->exclude('vendor')//排除的目录
            ->in([__DIR__.'/app/'])//检测的目录，支持多个目录
    )
;

```

