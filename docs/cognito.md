# Cognito

## Cognito Signup Validation

This page explains the Cognito signup validation flow integrated into the QuantixOne application.

---

## Signup Validation Workflow (Mermaid)
```mermaid
flowchart TD
    A[User Opens Signup Page] --> B[User Enters Signup Details]
    B --> C["Frontend Validation<br/>Name, DOB, Phone, Email, Aadhaar, PAN"]
    C -->|Valid| D["Amplify signUp()"]
    C -->|Invalid| C1[Show Validation Errors]
    
    D --> E["Cognito UserPool<br/>Validate Schema"]
    E -->|Missing / Invalid Attributes| E1[Return Error to UI]
    E -->|Success| F[User Created as CONFIRMED or UNCONFIRMED]
    
    F --> G["User Receives OTP / MFA<br/>if enabled"]
    G --> H[User Enters OTP in UI]
    H --> I["Amplify confirmSignUp()"]
    I -->|Success| J["Signup Completed<br/>Redirect to Login"]
    I -->|Failure| I1[Show Incorrect OTP Error]
```

---

## Signup Validation (Video)

The following video demonstrates the complete signup validation process:

<video controls width="800">
  <source src="https://dbmgw9llaznft.cloudfront.net/cognito-signup-validator.webm" type="video/webm">
  Your browser does not support the video tag.
</video>


## new page updated

The following text is autodeployed from github actions
