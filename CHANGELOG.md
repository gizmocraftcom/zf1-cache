# Changelog

## 2.0.0

Fork of `diablomedia/zendframework1-cache`, published as `gizmocraft/zendframework1-cache`.

### Breaking changes

- Requires PHP `>=8.5`. Tested on PHP 8.5 and 8.6.
- Package renamed from `diablomedia/zendframework1-cache` to `gizmocraft/zendframework1-cache`. It now requires `gizmocraft/zendframework1-exception` `^2.0.0`, `gizmocraft/zendframework1-config` `^3.0.0`, `gizmocraft/zendframework1-loader` `^2.0.0` and `gizmocraft/zendframework1-log` `^2.0.0`.

### Deprecated backends (kept, not removed)

- `Zend_Cache_Backend_Xcache`: the XCache extension has no release for PHP 8.5 or 8.6. The class stays in place, is marked `@deprecated` and is untested.
- `Zend_Cache_Backend_WinCache`: the WinCache extension has no release for PHP 8.5 or 8.6. The class stays in place, is marked `@deprecated` and is untested.

### Backends that need an extension (kept)

- `Zend_Cache_Backend_Apc` already supports APCu (`apcu_*` functions, used first when available) and needs no port. The `apc_*` fallback for the discontinued APC extension is unchanged. The `ext-apc` suggestion in `composer.json` is kept as upstream wrote it; the class works with `ext-apcu`.
- `Zend_Cache_Backend_Memcached` (ext-memcache) and `Zend_Cache_Backend_Libmemcached` (ext-memcached) are unchanged. Their tests need a running memcached server and the extensions, so they are skipped locally and run in CI (GitHub Actions memcached service).

### Other changes

- Dev dependencies upgraded (PHPUnit 13, PHPStan 2.3, php-cs-fixer 3.95, GrumPHP 2.27). Dropped `composer-require-checker`, which has no release for PHP 8.6.
- Tests migrated to PHPUnit 13 attributes. CI runs PHP 8.5 and 8.6.
- No public signature changes. The only library changes are docblocks.
