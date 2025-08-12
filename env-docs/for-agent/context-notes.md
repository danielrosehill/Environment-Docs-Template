# Context Notes for AI Agents

This file contains specific context and notes that AI agents should be aware of when operating in Daniel's environment.

## Current Environment State

### Recent System Changes
- Check `../for-human/environment-updates.md` for the latest system modifications
- Package installations/removals may affect tool availability
- Network configuration changes may impact service accessibility

### Known Issues & Workarounds
- **Virtual Environment**: Always verify activation before Python operations
- **Docker Networks**: Ensure `cloudflared` network exists for external routing
- **GPU Access**: ROCM is available but may require specific environment setup

## Task-Specific Context

### Python Development
```bash
# Preferred workflow
uv venv .venv
source .venv/bin/activate  # Always verify this step
uv pip install <packages>
```

### Docker Deployment
```bash
# Standard pattern for services with external access
docker network create cloudflared  # If not exists
docker run -d --name service --network cloudflared --hostname service:80 <image>
```

### Secret Management
```bash
# Retrieve secrets using 1Password CLI
op item get "API Key Name" --field password
```

## Environment-Specific Considerations

### Network Topology
- **Internal services**: Use 10.0.0.x addresses directly
- **External access**: Route through Cloudflare tunnels
- **Development**: Local Docker containers with unique hostnames

### Resource Utilization
- **CPU**: 12 cores available - suitable for parallel processing
- **RAM**: 64GB - can handle large datasets and multiple services
- **GPU**: Available for AI/ML workloads via ROCM
- **Storage**: BTRFS RAID5 - reliable but monitor I/O intensive operations

### Security Context
- **Sudo access**: Available but use judiciously
- **SSH keys**: Pre-configured for LAN device access
- **API keys**: Available via 1Password CLI (`op`)
- **Default privacy**: Assume private repositories unless specified

## Common Patterns

### AI/ML Workflows
1. **Local development**: Use Ollama with Llama 3.2
2. **Cloud inference**: Prefer OpenRouter over direct OpenAI
3. **GPU utilization**: ROCM available for local model training/inference
4. **Data handling**: Prefer local backups, use Hugging Face for datasets

### Web Development
1. **Static sites**: Deploy via Netlify CLI
2. **Dynamic services**: Docker + Cloudflare tunnels
3. **Authentication**: Assume Cloudflare auth by default
4. **Testing**: Local Docker containers for prototyping

### Infrastructure Management
1. **LAN services**: SSH access to 10.0.0.x hosts
2. **Container orchestration**: Docker on local machine
3. **External routing**: Cloudflare tunnels with unique hostnames
4. **Monitoring**: Use available system tools (htop, etc.)

## Troubleshooting Quick Reference

### Python Issues
1. **Import errors**: Check virtual environment activation
2. **Package not found**: Verify correct environment and installation
3. **Permission errors**: Check file permissions and sudo requirements

### Network Issues
1. **Service unreachable**: Verify LAN connectivity (ping 10.0.0.1)
2. **External access**: Check Cloudflare tunnel configuration
3. **Docker networking**: Ensure proper network attachments

### Development Issues
1. **Build failures**: Check available disk space and dependencies
2. **Performance**: Monitor CPU/RAM usage, consider parallel processing
3. **Authentication**: Verify CLI tool authentication status

## Best Practices Reminders

### Code Organization
- Keep repositories clean and organized
- Avoid creating unnecessary single-purpose scripts
- Use direct CLI commands when possible
- Document complex setups for future reference

### Resource Management
- Monitor system resources during intensive operations
- Use appropriate tools for the task complexity
- Prefer local processing when privacy/performance benefits exist
- Clean up temporary files and containers

### Communication
- Be direct and technical in responses
- Focus on task completion over conversation
- Provide clear explanations for complex operations
- Document significant changes or discoveries

## Emergency Procedures

### System Recovery
1. **Service failures**: Check Docker container status and logs
2. **Network issues**: Verify LAN connectivity and routing
3. **Authentication problems**: Re-authenticate CLI tools as needed
4. **Resource exhaustion**: Identify and terminate resource-heavy processes

### Data Protection
1. **Backup critical work**: Use local storage and cloud backups
2. **Version control**: Commit frequently to Git repositories
3. **Configuration preservation**: Document custom configurations
4. **Recovery planning**: Maintain recovery procedures for critical services

## Notes for Future Sessions

- Update this file with new discoveries and patterns
- Document recurring issues and their solutions
- Note changes in tool preferences or configurations
- Record successful deployment patterns for reuse