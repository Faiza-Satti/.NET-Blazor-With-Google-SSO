# .NET Blazor with Google SSO

A sample Blazor application demonstrating how to integrate **Google Single Sign-On (OAuth 2.0 / OpenID Connect)** authentication in a Blazor Server / WebAssembly project.
---

## ✅ Features

- Google authentication using OAuth 2.0 / OpenID Connect  
- Secure sign-in / sign-out flows  
- User claims retrieval (e.g. email, name)  
- Blazor UI components to show authentication state  
- Environment-based configuration (Development / Production)  

---

## 🛠 Prerequisites

Before you begin, ensure you have the following installed:

- [.NET SDK](https://dotnet.microsoft.com/) (version compatible with your project)  
- A Google Cloud (Console) project set up for OAuth credentials  
- A browser for testing  
- (Optional) SSL / HTTPS support for local development  

---

## 🧭 Setup & Configuration

1. **Register OAuth credentials on Google Console**  
   - Go to [Google API Console](https://console.developers.google.com)  
   - Create a new OAuth 2.0 Client ID credential  
   - Set the authorized redirect URI(s). For local dev, something like:  
     ```
     https://localhost:5001/signin-oidc
     ```  
   - Get the **Client ID** and **Client Secret**

2. **Configure your Blazor app**  
   - Open `appsettings.json` / `appsettings.Development.json`  
   - Add your `Google:ClientId` and `Google:ClientSecret`  
   - Add the redirect URL if needed  
   - Example:
     ```json
     "Authentication": {
       "Google": {
         "ClientId": "YOUR_GOOGLE_CLIENT_ID",
         "ClientSecret": "YOUR_GOOGLE_CLIENT_SECRET"
       }
     }
     ```

3. **Update `Program.cs` / startup configuration**  
   - Use `AddAuthentication().AddOpenIdConnect(...)`  
   - Configure scopes, authority, claim actions  
   - Add authorization policies if needed  

4. **Enable HTTPS locally**  
   - Ensure launch settings / Kestrel is set up for SSL  
   - Configure the redirect URIs accordingly  

---

## 🧩 How It Works

1. User clicks “Login with Google”  
2. The OAuth 2.0 flow is triggered — user is sent to Google’s login consent page  
3. After successful login, Google sends an authorization code to your redirect URI  
4. The app exchanges that code for tokens (ID token, access token)  
5. The middleware validates the ID token and creates a user principal with claims  
6. In your Blazor UI, you can check `AuthenticationState` to see if user is logged in, show name/email  
7. Logout revokes or signs out the user session  

---

## ▶️ Running the Application

```bash
# Clone the repo
git clone https://github.com/Faiza-Satti/.NET-Blazor-With-Google-SSO.git

# Navigate into project
cd .NET-Blazor-With-Google-SSO

# (Optional) Restore & build
dotnet restore
dotnet build
```

# Run
dotnet run
