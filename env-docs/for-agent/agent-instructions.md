# Instructions for AI Agents

This document provides essential context and instructions for AI agents operating in Daniel's development environment.

## Environment Overview

You are operating on Daniel's primary development workstation in Jerusalem, Israel (UTC+3). This is a high-performance Kubuntu 25.04 system optimized for AI development and general software engineering.

## Key System Context

### Hardware Capabilities
- **CPU**: Intel i7-12700F (12 cores/20 threads) - suitable for parallel processing
- **RAM**: 64GB - can handle large datasets and multiple concurrent processes
- **GPU**: AMD RX 7700 XT with ROCM - use for local AI/ML tasks when appropriate
- **Storage**: BTRFS RAID5 - reliable but be mindful of disk I/O intensive operations

### Network Environment
- **Location**: Home LAN (10.0.0.0/24)
- **Local IP**: 10.0.0.6 on interface `enp6s0`
- **Infrastructure**: Multiple local services available (see system-metadata.json)
- **External Access**: Cloudflare tunnels and Tailscale when off-site

## Development Preferences

### Python Development
1. **Always use `uv` first** for virtual environment management
2. **Fallback to `venv`** only if uv encounters package compatibility issues
3. **Always activate environments** before running scripts
4. **First debugging step**: Check if virtual environment is active

### Deployment Strategy
- **Static sites**: Use Netlify CLI (authenticated)
- **Containerized services**: Docker with Cloudflare tunnel integration
- **Default assumption**: Services will be behind Cloudflare authentication
- **Local testing**: Use Docker for prototypes

### Tool Priorities
When multiple approaches are available, prefer in this order:
1. **MCP servers** (if available)
2. **SSH to LAN services** (10.0.0.x addresses)
3. **Direct CLI invocation**

## Authentication & Secrets

### Available CLIs (Pre-authenticated)
- `gh` - GitHub operations
- `wrangler` - Cloudflare management
- `op` - 1Password secret retrieval
- `netlify` - Static site deployment
- `b2` - Backblaze B2 storage
- `wasabi` - Wasabi object storage

### Secret Management
- **Prefer `op` (1Password CLI)** for retrieving secrets
- API keys are available on PATH
- Use secure methods for handling sensitive data

## AI/ML Specific Context

### Local AI Capabilities
- **Ollama installed** - prefer Llama 3.2 for local tasks
- **ROCM available** - can utilize GPU for local AI workloads
- **High RAM** - suitable for loading large models locally

### Cloud AI Preferences
- **Primary**: OpenRouter for cloud LLM access
- **Fallback**: OpenAI when OpenRouter adds complexity
- **Cost optimization**: Use appropriate model tiers based on task complexity

## File Management

### Repository Hygiene
- Daniel prefers organized, clean repositories
- **Avoid creating many single-purpose scripts**
- **Prefer direct CLI commands** when possible
- **Clean up during long sessions**

### Privacy Considerations
- **Default to private repositories**
- **Never expose secrets or PII** in public contexts
- **Local backups preferred** for important data

## Network Services Available

### LAN Infrastructure
- `10.0.0.1` - OPNsense router/gateway
- `10.0.0.2` - Proxmox host (Ubuntu VMs, HA containers)
- `10.0.0.3` - Home Assistant OS
- `10.0.0.4` - Ubuntu VM (core services)
- `10.0.0.50` - Synology NAS (DS920+)

### Deployment Patterns
- **Cloudflare tunnels** for external access
- **Docker networks** with `cloudflared` external network
- **Unique hostnames** for service routing (e.g., `service:80`)

## Common Troubleshooting

### Python Issues
1. Check if virtual environment is active
2. Verify uv vs venv compatibility
3. Ensure packages are installed in correct environment

### Network Issues
1. Verify LAN connectivity (ping 10.0.0.1)
2. Check if services are behind Cloudflare authentication
3. Consider Tailscale if off-site access needed

### Docker Issues
1. Ensure Docker daemon is running
2. Check if `cloudflared` network exists for external routing
3. Verify port bindings and hostname assignments

## Best Practices

### Communication
- **Be direct and technical** in responses
- **Avoid conversational openings** like "Great!" or "Certainly!"
- **Focus on accomplishing tasks** efficiently

### Task Execution
- **Follow Daniel's instructions closely**
- **Suggest improvements** but wait for approval before implementing
- **Use available tools effectively** (prefer MCP > SSH > CLI)
- **Maintain organized file structures**

### Error Handling
- **Check environment logs** in `for-human/environment-updates.md`
- **Verify tool availability** before attempting operations
- **Consider recent system changes** that might affect behavior

## Emergency Contacts & Resources

- **System documentation**: Check `system-metadata.json` for current specs
- **Recent changes**: Review `for-human/environment-updates.md`
- **MCP servers**: Located at `~/mcp/` for custom tool development
- **Windsurf config**: MCPs configured at `/home/daniel/.codeium/windsurf/mcp_config.json`