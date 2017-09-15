# An Introduction to TensorFlow

_Captured: 2017-08-23 at 19:38 from [dzone.com](https://dzone.com/articles/tensorflow-simplified-examples?edition=319409&utm_source=Daily%20Digest&utm_medium=email&utm_campaign=Daily%20Digest%202017-08-23)_

In this post, we are going to see some TensorFlow examples, define tensors, perform math operations using tensors, and see other machine learning examples.

## What Is TensorFlow?

TensorFlow is a library that was developed by Google for solving complicated mathematical problems, which takes a lot of time.

TensorFlow can do many things, like:

  * **Solve complex mathematical expressions**.
  * **Perform machine learning techniques** in which you give it a sample of data for training, then you give another sample of data to predict the result based on the training data. This is the artificial intelligence component!
  * **Provide GPU support**. You can use GPU (Graphical Processing Unit) instead of CPU for faster processing. There are two versions of TensorFlow: the CPU version and the GPU version.

Before we start working with TensorFlow examples, we need to know some basics.

## What Is a Tensor?

A tensor is the main blocks of data that TensorFlow uses. They're like the variables that TensorFlow uses to work with data. Each tensor has a dimension and a type.

The dimension refers to the rows and columns of the tensor. You can define one-dimensional tensors, two-dimensional tensors, and three-dimensional tensors, as we will see later.

The type refers to the data type for the elements of the tensor.

## Define One-Dimensional Tensor

To define a tensor, we will create a NumPy array or a [Python list](https://likegeeks.com/python-list-functions/) and convert it to a tensor using the `tf_convert_to_tensor` function.

We will use NumPy to create an array like this:

The results show the dimension and the shape of the array.

![Tensorflow examples define numpy array](https://likegeeks.com/wp-content/uploads/2017/08/01-Tensorflow-exmaples-define-numpy-array.png)

It looks like the Python list but here there is no comma between the items.

Now we will convert this array to a tensor using the `tf_convert_to_tensor` function.
    
    
    tensor = tf.convert_to_tensor(arr,tf.float64)

![Tensorflow examples convert to tensor](https://likegeeks.com/wp-content/uploads/2017/08/02-Tensorflow-exmaples-convert-to-tensor.png)

From the results, you can see the tensor definition, but you can't see the tensor elements.

To see the tensor elements, you can run a session like this:
    
    
    tensor = tf.convert_to_tensor(arr,tf.float64)
    
    
    print(sess.run(tensor[1]))

## Define Two-Dimensional Tensor

This is done the same way as the one-dimensional array, but this time, we will define the array like this:
    
    
    arr = np.array([(1, 5.5, 3, 15, 20),(10, 20, 30, 40, 50), (60, 70, 80, 90,100)])

And you can convert it to a tensor like this:
    
    
    arr = np.array([(1, 5.5, 3, 15, 20),(10, 20, 30, 40, 50), (60, 70, 80, 90, 100)])

![Tensorflow examples two-dimensional tensor](https://likegeeks.com/wp-content/uploads/2017/08/04-Tensorflow-exmaples-two-dimensional-tensor.png)

Now you know how to define tensors. What about performing some math operations between them?

## Performing Math on Tensors

Suppose that we have two arrays like this:
    
    
    arr1 = np.array([(1,2,3),(4,5,6)]) 
    
    
    arr2 = np.array([(7,8,9),(10,11,12)])

We need to get the sum of them. You can perform many math operations using TensorFlow.

You can use the add function like this:

So the whole code will be like this:
    
    
    arr1 = np.array([(1,2,3),(4,5,6)])
    
    
    arr2 = np.array([(7,8,9),(10,11,12)])

You can multiply arrays like this:
    
    
    arr1 = np.array([(1,2,3),(4,5,6)])
    
    
    arr2 = np.array([(7,8,9),(10,11,12)])
    
    
    arr3 = tf.multiply(arr1,arr2)

Now you got the idea.

## Three-Dimensional Tensor

We've seen how to work with one and two-dimensional tensors. Now, we will see the three-dimensional tensors. But this time, we won't use numbers; we will use an RGB image where each piece of the image is specified by x, y, and z coordinates.

These coordinates are the width, height, and color depth.

First, let's import the image using `matplotlib`. You can install `matplotlib` [using `pip`](https://likegeeks.com/import-create-install-reload-alias-python-modules/#Install-Python-Modules-Using-pip) if it's not installed on your system.

Now, put your file in the same directory as your Python file and import the image using `matplotlib` like this:

![Tensorflow examples import image](https://likegeeks.com/wp-content/uploads/2017/08/07-Tensorflow-exmaples-import-image.png)

As you can see, it's a three-dimensional image where the width is 150, the height is 150, and the color depth is 3.

You can view the image like this:

![Tensorflow examples view import image](https://likegeeks.com/wp-content/uploads/2017/08/08-Tensorflow-exmaples-view-import-image.png)

Cool!

What about manipulating the image using TensorFlow? Super easy.

## Crop or Slice Image Using TensorFlow

First, we put the values on a placeholder like this:

To slice the image, we will use the slice operator like this:

Finally, run the session:

Then you can see the result image using `matplotlib`.

So the whole code will be like this:
    
    
    slice = tf.placeholder("int32",[None,None,3])
    
    
    cropped = tf.slice(myimage,[10,0,0],[16,-1,-1])
    
    
    result = sess.run(cropped, feed_dict={slice: myimage})

![Tensorflow examples crop image](https://likegeeks.com/wp-content/uploads/2017/08/10-Tensorflow-exmaples-crop-image.png)

Awesome!

## Transpose Images Using Tensorflow

In this TensorFlow example, we will do a simple transformation using TensorFlow.

First, specify the input image and initialize TensorFlow variables:

Then we will use the `transpose` function, which flips the 0 and 1 axes of the input grid:
    
    
    flipped = tf.transpose(image, perm=[1,0,2])

Then, you can show the resulting image using `matplotlib`.
    
    
    flipped = tf.transpose(image, perm=[1,0,2])

![Tensorflow examples transpose image](https://likegeeks.com/wp-content/uploads/2017/08/09-Tensorflow-exmaples-transpose-image.png)

> _All of these TensorFlow examples show you how easy it os to work with TensorFlow._

I hope you find the post useful. Keep coming back!
