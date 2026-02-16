# Google Services Configuration

This file explains how to set up Firebase credentials for development and production builds.

## Setup Instructions

1. **Copy the template:**
   ```bash
   cp google-services.example.json google-services.json
   ```

2. **Get your credentials from Firebase Console:**
   - Go to [Firebase Console](https://console.firebase.google.com/)
   - Select your project
   - Download `google-services.json`

3. **Configure for Development & Production:**
   - The file supports two clients:
     - **Production:** `com.tauhee56.travesocial` (Release builds)
     - **Development:** `com.tauhee56.travesocial.dev` (Debug builds)

4. **Build commands:**
   ```bash
   # Development build
   ./gradlew assembleDevDebug
   
   # Production build
   ./gradlew assembleProdRelease
   ```

## Important Notes

- **`google-services.json` is NOT committed** to Git (listed in `.gitignore`)
- Each developer needs their own local copy
- Never push this file to GitHub
- Contains sensitive API keys and OAuth credentials

## File Structure

```
{
  "project_info": { ... },
  "client": [
    {
      "client_info": {
        "package_name": "com.tauhee56.travesocial"
      },
      ...
    },
    {
      "client_info": {
        "package_name": "com.tauhee56.travesocial.dev"
      },
      ...
    }
  ]
}
```

Each client entry needs:
- `package_name`: Your app's package ID
- `oauth_client`: Authentication configuration
- `api_key`: Firebase API key
- `certificate_hash`: Android keystore fingerprint
