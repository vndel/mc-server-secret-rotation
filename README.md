# Minecraft Server Secret Rotation

Inventory and operational guidance for rotating credentials used by a Minecraft network. Never commit live secrets, sample real credentials, or paste secret values into tickets.

## Rotation workflow
1. Identify the credential owner, consumers, expiry, and recovery path without copying the secret value.
2. Create a replacement in the approved secret manager with least-privilege scope.
3. Update one consumer at a time, reload or restart safely, and verify health.
4. Revoke the old credential after all consumers have moved.
5. Confirm the old credential fails, review audit logs, and update the next-rotation date.

Prioritize exposed credentials immediately. For routine rotation, coordinate dependent services and retain a short, controlled rollback window where policy permits. Rotate RCON, database, cache, webhook, and deployment credentials independently. Avoid command-line arguments and shell history when injecting values.