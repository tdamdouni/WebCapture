# Algorithm outdoes radiologists at spotting pneumonia in X-rays

_Captured: 2017-11-18 at 00:59 from [www.futurity.org](http://www.futurity.org/x-rays-algorithm-pneumonia-1607282/?utm_source=feedly&utm_medium=webfeeds)_

A new algorithm called ChexNet can diagnose pneumonia from chest X-rays, researchers report.

The algorithm can diagnose up to 14 types of medical conditions and is able to diagnose pneumonia better than expert radiologists working alone.

"Interpreting X-ray images to diagnose pathologies like pneumonia is very challenging, and we know that there's a lot of variability in the diagnoses radiologists arrive at," says Pranav Rajpurkar, a graduate student in the Stanford University Machine Learning Group and co-lead author of a paper about the algorithm.

![Researchers look at X-rays and heat maps](http://www.futurity.org/wp/wp-content/uploads/2017/11/X-rays-algorithm-heat-maps_740.jpg)

> _A tool the researchers developed along with the algorithm produced these images, which are similar to heat maps and show the areas of the X-ray most indicative of pneumonia. (Credit: L.A. Cicero/Stanford)_

"We became interested in developing machine learning algorithms that could learn from hundreds of thousands of chest X-ray diagnoses and make accurate diagnoses," Rajpurkar says.

### Outperforming radiologists

The work uses a public dataset initially released by the National Institutes of Health Clinical Center on September 26. That dataset contains 112,120 frontal-view chest X-ray images labeled with up to 14 possible pathologies. It was released in tandem with an algorithm that could diagnose many of those 14 pathologies with some success, designed to encourage others to advance that work.

As soon as they saw these materials, the Machine Learning Group--a group led by Andrew Ng, adjunct professor of computer science at Stanford--knew it had found its next research direction.

> "…we believe that a deep learning model for this purpose could improve health care delivery across a wide range of settings…"

The researchers, working with Matthew Lungren, an assistant professor of radiology, had four radiologists independently annotate 420 of the images for possible indications of pneumonia.

The researchers have chosen to focus on this disease, which brings 1 million Americans to the hospital each year, according to the Centers for Disease Control and Prevention, and is especially difficult to spot on X-rays, the researchers say. In the meantime, the Machine Learning Group team got to work developing an algorithm that could automatically diagnose the pathologies.

Within a week the researchers had an algorithm that diagnosed 10 of the pathologies labeled in the X-rays more accurately than previous state-of-the-art results. In just over a month, their algorithm could beat these standards in all 14 identification tasks.

In that short time span, CheXNet also outperformed the four radiologists in diagnosing pneumonia accurately.

### The challenge of reading X-rays

Often, treatments for common but devastating diseases that occur in the chest, such as pneumonia, rely heavily on how doctors interpret radiological imaging. But even the best radiologists are prone to misdiagnoses due to challenges in distinguishing between diseases based on X-rays.

"The motivation behind this work is to have a deep learning model to aid in the interpretation task that could overcome the intrinsic limitations of human perception and bias, and reduce errors," explains Lungren, who is coauthor of the paper.

"More broadly, we believe that a deep learning model for this purpose could improve health care delivery across a wide range of settings," Lungren says.

After about a month of continuous iteration, the algorithm outperformed the four individual radiologists in pneumonia diagnoses. This means that the diagnoses provided by CheXNet agreed with a majority vote of radiologists more often than those of the individual radiologists.

The algorithm now has the highest performance of any work that has come out so far related to the NIH chest X-ray dataset.

### Focusing on the future

The researchers have also developed a computer-based tool that produces what looks like a heat map of the chest X-rays--but instead of representing temperature, the colors of these maps represent areas that the algorithm determines are most likely to represent pneumonia.

This tool could help reduce the amount of missed cases of pneumonia and significantly accelerate radiologist workflow by showing them where to look first, leading to faster diagnoses for the sickest patients.

In parallel to other work the group is doing with irregular heartbeat diagnosis and electronic medical record data, the researchers hope CheXNet can help people in areas of the world where people might not have easy access to a radiologist.

"We plan to continue building and improving upon medical algorithms that can automatically detect abnormalities and we hope to make high-quality, anonymized medical datasets publicly available for others to work on similar problems," says Jeremy Irvin, a graduate student in the Machine Learning group and co-lead author of the paper.

"There is massive potential for machine learning to improve the current health care system, and we want to continue to be at the forefront of innovation in the field."

A paper about the algorithm is available on [arXiv](https://arxiv.org/pdf/1711.05225.pdf).

Additional researchers contributing to this work are from the Machine Learning Group at Stanford University and the university's School of Medicine.
