<!-- ![AGRISISTANCE Logo](public/img/svg/logo.svg) -->
<div align="center">
  <img src="public/img/svg/logo.svg" alt="landing page"/>
</div>

# 🌱 AGRISISTANCE

**A2SV-Agrisistance** is an AI-driven web application aimed at helping African farmers optimize land use and boost crop productivity. Utilizing advanced machine learning algorithms and data analytics, AGRISISTANCE offers actionable insights and personalized recommendations tailored to individual farming needs.


## Features

### Optimizing Land Use

- 🌿 Analyzes soil properties, weather conditions, and historical crop data.
- 🌾 Provides recommendations for optimal crop selection and planting schedules.

### Boosting Crop Productivity

- 💧 Personalized advice on irrigation, fertilization, and pest management.
- 📈 AI-driven insights to enhance crop yields.

### Business Planning

- 💼 Financial forecasts, market trends, and cost-benefit analyses.
- 🗺️ Strategic planning and decision-making support.

### Resource Management

- 💧 Monitors water usage and tracks seed and fertilizer inventory.
- 📊 Tools for efficient resource management.

### Networking and Industrial Connections

- 🌍 Connects farmers with related industries, such as delivery services and processing factories.
- 🔗 Streamlines supply chain processes and builds valuable industrial connections.

## Getting Started

Follow these steps to set up and run the AGRISISTANCE project locally:

### Prerequisites

Before you begin, ensure you have the following installed:

- [Node.js](https://nodejs.org/): This project requires Node.js to run. Download and install it from [nodejs.org](https://nodejs.org/).
- [Git](https://git-scm.com/): You’ll need Git to clone the repository. Download and install it from [git-scm.com](https://git-scm.com/).

### Cloning the Repository

1. **Clone the repository**: Open your terminal or command prompt and run the following command:

    ```bash
    git clone https://github.com/AGRISISTANCE/Agrisistance-Backend.git
    ```

2. **Navigate to the project directory**:

    ```bash
    cd Agrisistance-Backend
    ```

### Installing Dependencies

1. **Install project dependencies**: Run the following command to install all the required npm packages:

    ```bash
    npm install
    ```

### Setting Up Environment Variables

1. **Create a `.env` file** in the root directory of the project with the following structure:

    ```plaintext
    MYSQL_HOST=''
    MYSQL_USER=''
    MYSQL_PASSWORD=''
    MYSQL_DATABASE=''

    MYSQL_DELETION_HOST = ''
    MYSQL_DELETION_USER = ''
    MYSQL_DELETION_PASSWORD = ''
    MYSQL_DELETION_DATABASE = ''

    EMAIL_USER=''
    EMAIL_PASSWORD='' 

    GOOGLE_CLIENT_ID=''
    GOOGLE_CLIENT_SECRET=''
    GOOGLE_REDIRECT_URI=''
    AGRISISTANCE_REDIRECT_URI=''
    GOOGLE_REFRESH_TOKEN=''

    TWILIO_SID=''
    TWILIO_API_KEY=''

    STRIPE_SECRET_KEY=''

    TOMMOROW_API_KEY='' 

    JWT_SECRET='' 

    CLOUDINARY_CLOUD_NAME=''
    CLOUDINARY_API_KEY=''
    CLOUDINARY_API_SECRET=''

    PORT=''
    ```

2. **Explanation of Environment Variables**:

    - `MYSQL_HOST`: The machine where the database is running.
    - `MYSQL_USER`: The user account that owns the database.
    - `MYSQL_PASSWORD`: The password for the user account.
    - `MYSQL_DATABASE`: The name of the database.

    - `EMAIL_USER`: The email address that will be used to send emails to clients.
    - `EMAIL_PASSWORD`: The password for the email account.

    **Google Authentication and Email Sending Setup**

    To enable Google authentication and email sending, follow these steps:

    1. **Go to Google Cloud Console**: 
        - Visit the [Google Cloud Console](https://console.cloud.google.com/) and log in with your Google account.
        - Create a new project by selecting the dropdown in the top left and clicking on “New Project.”

    2. **Enable Google+ API**:
         - Once the project is created, navigate to the **Library** section on the left sidebar.
        - Search for **Google+ API** and click on it.
        - Click **Enable** to activate the API for your project.

    3. **Set Up OAuth Consent Screen**:
        - In the left sidebar, go to **OAuth Consent Screen**.
        - Choose **External** and click **Create**.
        - Fill out the required fields on the first page of the form:
            - **App Name**: Enter the name of your application.
            - **User Support Email**: Select your email address.
            - **Email Addresses**: Add your email to the developer contact information.
        - Skip the other pages of the form; there's no need to fill them out unless required.
        - **Important**: Avoid uploading an application logo, as this may trigger Google's verification process, which can take additional time.
        - Click **Save and Continue** until the consent screen is configured.

    4. **Publish the App**:
        - After setting up the OAuth Consent Screen, you'll be in the "Test" phase by default.
        - Click **Publish App** to move your app from testing to production.

    5. **Create OAuth Client ID Credentials**:
        - Go to the **Credentials** section in the left sidebar.
        - Click **Create Credentials** and select **OAuth Client ID**.
        - Set **Application Type** to **Web Application** and provide a name for the credentials.
         - In the **Authorized JavaScript origins** section, add `http://localhost:PORT     /` (replace `PORT` with the port number your application will use).
         - In the **Authorized redirect URIs** section, add the following two URIs:
           - **GOOGLE_REDIRECT_URI**: `https://developers.google.com/oauthplayground`
           - **MY_REDIRECT_URI**: `http://localhost:PORT/api/auth/google/callback`
         - The first URI is for internal service use (email functionality), and the      second is where users will be redirected after Google authentication.
         - Click **Create**.

    6. **Add Client ID and Client Secret to .env**:
        - Once the credentials are created, you will receive the **GOOGLE_CLIENT_ID** and **GOOGLE_CLIENT_SECRET**.
        - Add these values to your `.env` file:
         ```bash
         GOOGLE_CLIENT_ID='your-google-client-id'
         GOOGLE_CLIENT_SECRET='your-google-client-secret'
         ```

    7. **Generate Google Refresh Token**:
        - The refresh token is necessary for email functionality (sending emails).
        - Visit the [OAuth Playground](https://developers.google.com/oauthplayground).
        - In the left section, scroll down to **Step 1** and enter the following scope: `https://mail.google.com`.
        - At the top right, click on the settings icon and check **Use your own OAuth       credentials**.
        - Enter your **GOOGLE_CLIENT_ID** and **GOOGLE_CLIENT_SECRET** from the `.env`      file.
        - Click **Authorize APIs** and proceed through the account selection and        consent screens.
        - In **Step 2**, click **Exchange authorization code for tokens**.
        - In **Step 3**, click **Refresh access token** to get the refresh token.
        - Copy the refresh token and add it to your `.env` file:
         ```bash
         GOOGLE_REFRESH_TOKEN='your-refresh-token'
         ```
         - Ignore the access token since it expires after one hour; your server will generate it as needed using the refresh token.
   
   ### 

    - `TWILIO_SID` and `TWILIO_API_KEY`: Sign in to [Twilio](https://www.twilio.com/) and generate these from the API section.

    - `STRIPE_SECRET_KEY`: Log in to [Stripe](https://stripe.com/) and generate a secret key from the API section.

    - `TOMMOROW_API_KEY`: Obtain your API key from [Tomorrow.io](https://www.tomorrow.io/).

    - `JWT_SECRET`: Generate a strong 256-bit character string for securing JWT tokens.

    - `CLOUDINARY_CLOUD_NAME`, `CLOUDINARY_API_KEY`, `CLOUDINARY_API_SECRET`: Sign in to [Cloudinary](https://cloudinary.com/) and generate these from the API section.

### Running the Application

1. **Start the development server**: After setting up the `.env` file and installing dependencies, start the server with:

    ```bash
    npm start
    ```

2. **Access the application**: Open your web browser and navigate to `http://localhost:8081` (default port is 8081).

### Troubleshooting

- **Common Issues**: If you encounter any issues during setup, ensure that all dependencies are installed correctly and check the console for error messages. You can also refer to the [GitHub Issues](#github-issues) page for known issues and solutions.

By following these steps, you should have AGRISISTANCE up and running on your local machine. If you need further assistance, please refer to the [Contact](#contact) section for support.


## Our Perspective

- 🌐 **Virtual Farm System Integration:** Simulate different scenarios for informed decision-making.
- 📱 **Mobile Application Development:** Enhance accessibility and usability through mobile platforms.

## Comparison with Competitors

| Feature                               | AGRISISTANCE | Intellias | OneSoil |
| ------------------------------------- | ------------ | --------- | ------- |
| AI-driven insights                    | ✅            | ✅         | ✅       |
| Personalized recommendations          | ✅            | ✅         | ✅       |
| Networking and industrial connections | ✅            | ❌         | ❌       |
| Resource management tools             | ✅            | ❌         | ❌       |
| Virtual farm system (future)          | ✅            | ❌         | ❌       |

## Contact

For inquiries or feedback, reach out to us at:

- 📧 Email: [ma_fellahi@esi.dz](mailto:ma_fellahi@esi.dz)
- 🌐 WhatsApp: +213 551 61 19 83
- **GitHub :** [flh-raouf](https://github.com/flh-raouf)

## License

This project is licensed under the Apache 2.0 License. See the [LICENSE](License.txt) file for details.

---



