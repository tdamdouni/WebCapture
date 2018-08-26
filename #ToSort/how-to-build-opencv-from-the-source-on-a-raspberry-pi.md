# How to Build OpenCV From the Source on a Raspberry Pi

_Captured: 2018-07-31 at 22:41 from [dzone.com](https://dzone.com/articles/how-to-deploy-opencv-on-raspberry-pi-enabling-mach?edition=385308&utm_source=Zone%20Newsletter&utm_medium=email&utm_campaign=iot%202018-07-31)_

To start building the OpenCV library from source code on Raspberry Pi, you'll first need to install development libraries.

### How to Install Development Libraries

Type these commands on the Raspberry Pi terminal:

You also need to install the required matrix, image, and video libraries:

The next step is to download the OpenCV source code via Git:

Using a Python virtual environment, deploy the OpenCV on Raspberry Pi with virtualenv. The benefit of this approach is that it isolates the existing Python development environment.

Check out these links below t0 learn more:

[How to build a home surveillance system using Raspberry Pi and camera](https://www.survivingwithandroid.com/2018/06/how-to-build-a-surveillance-system-with-raspberry-pi-3.html)

[How to build an IoT system using Raspberry Pi](https://www.survivingwithandroid.com/2016/12/raspberry-pi-iot-project-using-artik.html)

### Install and Configure Virtualenv for OpenCV

If your Raspbian hasn't installed it yet, you can install it using pip:

Then, you can configure a virtualenv in your bash profile:

Now, add the following scripts:

Next, save your bash profile file when finished. To create a Python virtual environment, type this command:

This command will create a Python virtual environment called **cv**. If you're using Python 3, you can create the virtual environment with the following command:

You should see (cv) on your terminal. If you close the terminal or call a new terminal, you'd have to activate your Python virtual environment again:

The following screenshot shows a sample Python virtual environment form called cv:

![https://www.packtpub.com/graphics/9781786466518/graphics/B05664_03_02.jpg](https://www.survivingwithandroid.com/wp-content/uploads/2018/07/https-www-packtpub-com-graphics-9781786466518-gr.jpeg)

Inside the Python virtual terminal, continue installing NumPy as the required library for OpenCV Python. You can install the library using pip:

Now, you're ready to build and install OpenCV from the source. After cloning the OpenCV library, you can build it by typing the following commands:

Next, install the OpenCV library on your internal system from Raspbian OS:

When you are done, you will have to configure the library so that Python can access it through Python binding. The following is a list of command steps for configuring with Python 2.7:

If you're using Python 3.x (say, Python 3.4), perform the following steps on the terminal:

The installation process is over.

### Verifying the OpenCV Installation on Raspberry Pi

Now, you need to verify whether OpenCV has been installed correctly by checking the OpenCV version:

You should see the OpenCV version on the terminal. A sample program output is shown in the following screenshot:

![how to install opencv on raspberry pi](https://www.survivingwithandroid.com/wp-content/uploads/2018/07/how_to_install_opencv_on_raspberry_pi.jpg)

> _How to use OpenCV to Enable Computer Vision_

The next demo displays an image file using OpenCV. For this scenario, you can use the `cv2.imshow()` function to display a picture file. For testing, log into the Raspberry Pi desktop to execute the program. Type the following script on a text editor:

Here, circle.png has been used as a picture source; you can use whichever file you want. Save the script into a file called `ch03_hello_opencv.py`; now, open the terminal inside your Raspberry Pi desktop and type this command:

If successful, you should see a dialog that displays a picture:

![opencv running on raspberry pi](https://www.survivingwithandroid.com/wp-content/uploads/2018/07/opencv_running_on_raspberry_pi.jpg)

The picture dialog shows up because you called `cv2.waitKey(0)` in the code. Press any key to close the dialog.

Lastly, close the dialog by calling the `cv2.destroyAllWindows()` function after receiving a click event. And, there you have it!
