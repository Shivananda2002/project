# Anima Project

Welcome! This project has been automatically generated by [Anima](https://animaapp.com/).

## Getting started

> **Prerequisites:**
> The following steps require [NodeJS](https://nodejs.org/en/) to be installed on your system, so please
> install it beforehand if you haven't already.

To get started with your project, you'll first need to install the dependencies with:

```
npm install
```

Then, you'll be able to run a development version of the project with:

```
npm run dev
```

After a few seconds, your project should be accessible at the address
[http://localhost:5173/](http://localhost:5173/)


If you are satisfied with the result, you can finally build the project for release with:

```
npm run build
```

## OTP Authentication Setup

This app uses Twilio Verify API for OTP authentication. To set up the backend:

### Backend Requirements

Create a backend server with the following endpoints:

1. **POST /send-otp**
   ```json
   {
     "phone": "+91XXXXXXXXXX"
   }
   ```
   Response:
   ```json
   {
     "success": true,
     "message": "OTP sent successfully"
   }
   ```

2. **POST /check-otp**
   ```json
   {
     "phone": "+91XXXXXXXXXX",
     "code": "123456"
   }
   ```
   Response:
   ```json
   {
     "valid": true,
     "message": "OTP verified successfully"
   }
   ```

### Environment Configuration

1. Copy `.env.example` to `.env`
2. Update `VITE_API_BASE_URL` with your backend URL:
   - For Bolt preview: Use `/api` (relative path)
   - For local development with ngrok:
   ```bash
   ngrok http 3001
   ```
   Then update the URL in `.env` to your ngrok URL
3. For production: Use your deployed backend domain

### Twilio Setup

1. Create a Twilio account
2. Get your Account SID, Auth Token, and Verify Service SID
3. Configure these in your backend environment

### Features

- ✅ Country code selection
- ✅ 6-digit OTP input
- ✅ Automatic OTP verification
- ✅ Resend OTP functionality
- ✅ Error handling and user feedback
- ✅ Loading states
- ✅ Mobile responsive design
