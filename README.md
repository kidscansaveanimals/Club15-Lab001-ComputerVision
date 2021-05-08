# Custom Vision - Workshop

Hi everyone and welcome!
In this tutorial you are going to create a Machine Learning model that can identify an object that you hold in front of a camera.

## Background Concept

Before we get started, let's learn about "why" you would do this in the first place.
The short answer is, using machine learning teaches the camera to "see." It doesn’t really see but the model inside of it makes it intelligent and can detect objects it is looking for.

## Let’s walk through an example that you will learn how to build in this lab using fruit

The camera is pointing at some fruit.  
Without any machine learning on your camera, you will just see a video recording of fruit.  

**How does anyone learn anything?**  

Think of when you were young before you could read. These are the steps you used to learn:

- You would be shown a flash card with a picture on it or you were given an object to feel.
- The object was an Apple.
- Next to the picture was written the word “Apple” or it was written in braille for you.

**This** is how you learned to connect the word to the object in the picture.

Teaching a computer to know what an apple is **works the same way**.

You show it a lot of pictures and tell it those are apples.  Then, to put it simply, it makes a little program that you can install on your camera.  Once you do, if your camera could talk, it would say, “I am now smart enough to know when I see an apple come into view.”
That is called *“training the model.”*  In this lab you will “train the model” to identify fruit.

## From Apples to Elephants

Once you complete the steps in this lab, which uses fruit as an example, there is conceptually no difference between whether you taught the computer so know apples, oranges, cats, or elephants.
Like learning to ride a bike.  
Once you know the basics, you can ride all sorts of different bikes using the same concepts of pedaling, balancing, steering, and ringing a bell to make sure people know you are coming their way.
Just takes some practice and in no time, you are on your way!

## How do Camera Traps work?

They work the same way!  

The scientist trains the machine learning model to identify something, like a Snow Leopard. Then that model is put on the smart camera and runs on it. Every picture the camera takes through its lens is sent to the model and is looked at just waiting to see if a picture is a snow leopard.  

It would go something like this, if you can imagine a camera could talk:

1. **Camera:**  
    "just waiting here… sending every snap shot I see through a machine learning model I was given… nothing much going on today…"
1. **The ML Model inside the camera:**  
    "Nope. Nope. Nope. Nothing to see here. Nope. Nothing I know."  
  
1. *The Snow Leopard walks by.*  

1. **Camera:**  
    "Still sending everything I see to my friend the ML model"
1. **The ML Model inside the camera:**  
    "Wait… waaaaaait… I know this… OMGOSH! I KNOW WHAT THAT IS! I WAS TRAINED FOR THIS! THAT IS A SNOW LEOPARD!!!!"

So that’s what a camera trap is doing, waiting to see something it recognizes using a little program you trained to identify the object.  
In a future lab we will learn how the camera acts once an object is identified and tells the rangers.

You can learn more about how camera traps are used in the wild by listening to the Club 15 interview with Dr. Eric Dinerstein.

## LET'S GO\!

### 1. Getting an Azure Subscription

To run this tutorial you need to have an Azure Subscription. If you are a minor you should ask one of your parents or a guardian to help you with signing up. If you are above 13 years old you might be able to use the [Microsoft Azure for Students Starter Offer](https://azure.microsoft.com/offers/ms-azr-0144p/?WT.mc_id=aiml-25242-heboelma)

To sign up for an Azure Subscription [Click here](https://azure.microsoft.com/free/?WT.mc_id=aiml-25242-heboelma)

### 2. Build a fruit classifier project

Now we can build our classifier! navigate to [https://www.customvision.ai](https://www.customvision.ai/?WT.mc_id=aiml-25242-heboelma).

1. Navigate to [https://www.customvision.ai](https://www.customvision.ai/?WT.mc_id=aiml-25242-heboelma)

    ![Custom Vision Sign in](images/CustomVision-01.png)

1. Sign in with your Azure account credentials.
1. Accept **Terms of Service**

    ![Custom Vision Terms](images/CustomVision-02.png)

1. Click `NEW PROJECT` to create a new project  

    ![Custom Vision New Project](images/CustomVision-03.png)

1. Click `create new`

    ![Custom Vision New Project](images/CustomVision-04.png)

1. Create a **Resource Group**  

    Resource group provides a way to organize services.  In this lab, we will create multiple services including Custom Vision.  We will create all resources in the **Resource Group**

    Click `create new`  

    ![Custom Vision New Resource Group](images/CustomVision-05.png)

1. Give a name to a new resource group and select location

    > [!TIP]  
    > You can see locations in a map at <https://azure.microsoft.com/en-us/global-infrastructure/geographies/>  

    ![Custom Vision New Resource Group](images/CustomVision-07.png)

    | Item           | Value                                                                               |
    |----------------|-------------------------------------------------------------------------------------|
    | Name           | Name of the resource group.  E.g. Club15-ComputerVision                             |
    | Location       | Select a location nearest to you. Pick the same location as the new resource group. |

1. Click `Create resource group` to create a new resource group

1. Fill out information for the new project

    ![Custom Vision New Resource Group](images/CustomVision-06.png)

    | Item           | Value                                                                               |
    |----------------|-------------------------------------------------------------------------------------|
    | Name           | Name of the project.  E.g. Club15-Fruit-Project                                     |
    | Subscription   | Select your Azure subscription                                                      |
    | Resource Group | Select the resource group just created.  E.g. Club15-ComputerVision                 |
    | Kind           | Cognitive Service                                                                   |
    | Location       | Select a location nearest to you. Pick the same location as the new resource group. |
    | Pricing Tier   | S0                                                                                  |

1. Click `Create resource`

1. Fill out information to create a new Custom Vision project

    ![Custom Vision New Project](images/CustomVision-08.png)

    | Setting              | Value                                                                              |
    |----------------------|------------------------------------------------------------------------------------|
    | Name                 | Fruit Project                                                                      |
    | Description          | Add a description of the classifier (example shown in image above)                 |
    | Resource             | Choose the resource you created in the previous step.   E.g. Club15-Fruit-Project  |
    | Project Type         | Classification                                                                     |
    | Classification Types | Multiclass (Single tag per image)                                                  |
    | Domains              | Food (compact)                                                                     |
    | Export Capabilities  | Basic platforms                                                                    |
  
1. Click `Create project` to create a new project

### 3. Add training images

Now you can start adding images and assigning them tags to create our image classifier.

1. Click [Fruit dataset](https://github.com/aiadvocates/Fruit-Dataset/raw/main/fruit.zip) to download `fruit.zip` file
1. Unzip `fruit.zip` to your computer
  
    e.g. C:\fruit

1. Open Fruit Project in your browser, then click `Add images`

    ![Custom Vision Add Images](images/CustomVision-09.png)

1. Select the folder you unzipped Fruit.zip file

    E.g. C:\Fruit

    ![Custom Vision Add Images Folder](images/CustomVision-10.png)

1. Select folder `apple`, then select all images, click `Open` to upload all apple images

    ![Custom Vision Add Images Folder](images/CustomVision-11.png)

1. Add the tag 'Apple' then click `Upload 10 files`  

    ![Custom Vision Add Images Tag](images/CustomVision-12.png)

1. Confirm 10 images are upload

    ![Custom Vision Add Images Tag](images/CustomVision-13.png)

1. Repeat the same steps for other fruits

    ![Custom Vision Add Images Tag](images/CustomVision-14.png)

Now you should have all categories uploaded and on the left hand side you can see your fruit classes and you can filter depending on type of fruit.

![Custom Vision Upload Done](images/CustomVision-15.png)

### 4. Train Model

Now you are ready to train your model on the fruit image data you have uploaded.

1. Click the green `gear icon` in the top right corner.  

    For this lab, you can use the "Quick Training" option.

    ![Custom Vision Upload Done](images/CustomVision-16.png)

1. Wait until the training completes

    Training takes a few minutes.

    ![Custom Vision Training](images/CustomVision-17.png)

    Once the training process is complete it will take you to the Performance tab. Here you will receive machine learning evaluation metrics for your model.

    ![Custom Vision Training Done](images/CustomVision-18.png)

### 5. Test Machine Learning Model

Now you have a model, you need to test the model. Choose the 'Quick Test' button in the top right *(next to the train button)* this will open a window where you can browse for a local image or enter a web URL.

Use one of the image links below (these are images the model has not been trained on) and paste the link in the Image URL field. The image will be analysed and a result returned of what Fruit the model thinks it is (prediction tag) and the models confidence of its result (prediction probability).

<https://github.com/aiadvocates/Fruit-Dataset/raw/main/test/apple.jpg>

![Custom Vision Quick Test](images/CustomVision-19.png)

The machine learning model evaluates (sees) images and tell what they are.

E.g.  The machine learning says this image is apple with 96.7% confidence.

![Custom Vision Quick Test](images/CustomVision-20.png)

> [!TIP]  
> Repeat this process for other image in the test folder, or search online for other images to see how the model performs.  
> <https://github.com/aiadvocates/Fruit-Dataset/raw/main/test/apple.jpg>  
> <https://github.com/aiadvocates/Fruit-Dataset/raw/main/test/banana.jpg>
> <https://github.com/aiadvocates/Fruit-Dataset/raw/main/test/orange.jpg>
> <https://github.com/aiadvocates/Fruit-Dataset/raw/main/test/pineapple.jpg>

Now you have trained a model that can see the difference between 4 fruits.  
Feel free to take out your camera and add an other fruit, or maybe create a completely different model.

Ideas for other models to make using pictures:

- Your pets - Imagine a camera that you could tell which pet was sleeping in your bed!
- Wild animals you like - Just like a real life use case to protect animals!
- Different toys!

## Use your model in the real world

In this last part we are going to take the model you have created and use it in an application that uses your camera and the machine learning model.

The goal is to hold an apple in front of your webcam and the application will tell you if it is a apple or not.

### 1. Download the model

In this step we are going to export the model as a TensorFlow.js model.

1. Click on Performance in the top menu
1. Click on Export
1. Click on TensorFlow

    ![Custom Vision Model Export](images/CustomVision-21.png)

1. In the dropdown box select TensorFlow.js

    ![Custom Vision Model Export to TensorFlow.js](images/CustomVision-22.png)

1. Click Export (Wait a few seconds for the model to be ready for export)

    ![Custom Vision Model Export](images/CustomVision-23.png)

1. Click Download

    ![Custom Vision Model Download](images/CustomVision-24.png)

> [!TIP]  
> Now you should have received a .zip file with a long name.

### 2. Setup the Web Application (WebApp)

In this step we are going to run a simple webapp and upload the downloaded model to it.
Click the button below to start the deployment of a web application in your Azure Subscription.  

> [!NOTE]  
> Don't worry, the webapp is using the **free** tier of Azure WebApps so it will not cost you money.

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faiadvocates%2FCustomVision-Workshop%2Fmain%2Fdeployment%2Ftemplate.json)

After clicking the button and assuming you are successfully logged in in Azure, you should see the screen below.

1. Fill in the missing fields:

    ![Deploy ARM Template](images/WebApp-01.png)

    | Item           | Value                                                                        |
    |----------------|------------------------------------------------------------------------------|
    | Subscription   | Select your Azure subscription                                               |
    | Resource group | Select the previously created Resource group. E.g. Club15-ComputerVision     |
    | Region         | Should be automatically selected based on your Resource Group location       |
    | Web App Name   | Enter a name (like: club15-maya or club15-yourName), no spaces allowed.      |

    > [!TIP]  
    > The name of WebApp must be globally unique, meaning, only one in the world.  So be creative!

1. Click `Review + Create`  

    Azure portal checks a few things before start deploying.

1. Click `Create`

    ![Deploy ARM Template Create](images/WebApp-02.png)

    Now you can take a 5 minute break.
    When the deployment is complete you see the message: "Your deployment is complete".

    ![Deploy ARM Template Create Progress](images/WebApp-03.png)

### 3. Access WebApp

Let's find the address of WebApp.

1. Click `Go to resource group`  

    ![Deploy ARM Template Complete](images/WebApp-04.png)

    In the resource group, you should see 3 items.  (These are called resources).

    - App Service Plan : For WebApp
    - App Service : For WebApp
    - Cognitive Service : For Custom Vision project

1. Click on the `App Service` Item

    This item should have the same name as you entered in the steps before. (Like: club15-maya or club15-yourName)

    ![Deploy ARM Resource Group](images/WebApp-05.png)

1. Access the WebApp by clicking `URL`  

    Your WebApp is now up and running and you can now upload your model and test it!

    ![Deploy ARM App Service](images/WebApp-06.png)

1. The first time it may take 30 seconds or so but you should see :

    ![Deploy ARM WebApp](images/WebApp-07.png)

### 4. Upload Machine Learning Model

1. Click `Choose File`
1. Select the zip file you have downloaded in the previous step. (The one with the long file name.)
1. Click `Upload`

![Deploy ARM WebApp](images/WebApp-08.png)

### 5. Show your fruits to Machine Learning\!

1. When the upload is complete the browsers asks to access your camera. Click "Allow"

    ![Deploy ARM WebApp](images/WebApp-09.png)

1. On the screen you should now see your camera
1. Go to the kitchen and pick an apple or banana and hold it in front of the camera.

    ![Deploy ARM WebApp Apple](images/WebApp-10.png)
