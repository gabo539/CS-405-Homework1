# CS405 Project 1: 3D Animations using ChatGPT

## Report by Ralf-Gabriel Porębski

### Task 1:

#### Screenshot:

SEE REPORT FILE!

#### ChatGPT link: https://chatgpt.com/share/670fa464-e4e0-800a-8566-85e8c8e7f726

#### Task report:

I followed the exact instructions of the Task. At first I got an explanation by in words by ChatGPT and later followed the code (see link). I pasted the code and uncommented the line necessary in the "index.html file". The result (s. screenshot) seems rather odd to me and assume that my suspicion got confirmed in Task 2, as the result of my calculation is different.

### Task 2:

#### Screenshot:

SEE REPORT FILE!

#### Task reports:

##### Code fragment:

```js
/**
 * 
 * @TASK2 Calculate the model view matrix by using the given 
 * transformation methods and required transformation parameters
 * stated in transformation-prompt.txt
 */
function getModelViewMatrix() {
    const translationMatrix = createTranslationMatrix(0.3,-0.25, 0); // Translation by 0.3 units in x-axis and -0.25 units in y-axis
    const scaleMatrix = createScaleMatrix(0.5, 0.5, 1);             // Scaling by 0.5 in x and y axes
    const rotationMatrixX = createRotationMatrix_X(0.523598776);    // Rotation by 30 degrees in x-axis
    const rotationMatrixY = createRotationMatrix_Y(0.785398163);    // Rotation by 45 degrees in y-axis
    const rotationMatrixZ = createRotationMatrix_Z(1.04719755);     // Rotation by 60 degrees in z-axis

    //const modelViewMatrix = multiplyMatrices(multiplyMatrices(multiplyMatrices(multiplyMatrices(translationMatrix, scaleMatrix), rotationMatrixX), rotationMatrixY), rotationMatrixZ); // given order
    const modelViewMatrix = multiplyMatrices(multiplyMatrices(multiplyMatrices(multiplyMatrices(scaleMatrix,rotationMatrixX), rotationMatrixY), rotationMatrixZ), translationMatrix); //my order

    return modelViewMatrix;
}
```

At first i create the transition matrix according to the metric given. Later on I do the same with the scaling. I scale by the z-axis with the value 1, as this keeps the skaling neutral. Then I rotate seperately for around each axis. I saw that the input has to be in radian, so I looked up the values for the given degrees on the Internet.

In the end I multiplied the matrices according to a order different to the given one, therefore I performed a right-sided multiplication of each rotation matrix on the scale matrix and afterwards a I applied the translationMatrix. The reason for that is that I have found online sources ([Why Transformation Order Is Significant - Windows Forms .NET Framework | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/advanced/why-transformation-order-is-significant?view=netframeworkdesktop-4.8)[Why Transformation Order Is Significant - Windows Forms .NET Framework | Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/desktop/winforms/advanced/why-transformation-order-is-significant?view=netframeworkdesktop-4.8)) which state that the order here matters, since rotations and scalations are connected to the origin. Therefore a translation should be performed last. In the End I return the result of the multiplication. But the outcommented matrix multiplication which follows the given order returns a pretty similiar result.

The result is different from the result ChatGPT generated in Task 1. Since I checked my calculation in details, I assume that my calculation is right. ChatGPT may have explained me the task correctly, but it failed to perform the calculation itself. This is tipical behaviour for a LLM.

### Task 3:

#### Screenshots:

SEE REPORT FILE!

#### ChatGPT link: https://chatgpt.com/share/670fa464-e4e0-800a-8566-85e8c8e7f726

#### Report:

I have completed the task with ChatGPT according to the instructions. I copied the provided code (s. project files) and after revising the code and seeing the animation on my webbrowser I came to the conclusion that the provided code is correct.
