# Generate Tags

**Internal Action** - Generates image tags for matrix builds in monorepo workflows.

## Purpose

This action is used internally for monorepo matrix builds to generate appropriate tags for each service. Not intended for direct use.

## Usage

```yaml
# Internal use in matrix workflows
- uses: KoalaOps/generate-tags@v1
  with:
    services_config_path: services.json
    tag_format: branch-date-counter
    branch: main
```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `services_config_path` | Path to services.json file | ❌ | `services.json` |
| `service_name` | Single service name (when not using services.json) | ❌ | - |
| `tag_format` | Tag format: branch-date, branch-date-counter, semver, custom | ❌ | `branch-date-counter` |
| `branch` | Branch name for tag generation | ❌ | `${{ github.ref_name }}` |
| `custom_base_tag` | Custom base tag (used when tag_format is custom) | ❌ | - |

## Outputs

| Output | Description |
|--------|-------------|
| `tags` | JSON object mapping service names to tags |
| `base_tag` | Base tag used for all services |

## Note

This is an internal action for monorepo matrix builds. Use `determine-image-tag` action for standard tag generation.