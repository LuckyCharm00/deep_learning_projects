# CAPTCHA from a DeepLearning Perspective

The term CAPTCHA is an acronym for completely automated public Turing test to tell
computers and humans apart. This is a computer program that intends to distinguish
between a human user and a machine or a bot, typically as a security measure to prevent
spam and data misuse.


#### Goal 
- [x] Breaking CAPTCHAs using deep learning to expose their vulnerability
- [x] Generating CAPTCHA using adversarial learning

#### Dataset Link
Not Applicable  


#### Command to Generate Captcha using Claptcha package 

```bash
python CaptchaGenerator.py --outdir_train '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_train/' --num_captchas_train 16000 --outdir_val '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_val/' -- num_captchas_val 4000 --outdir_test '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_test/' --num_captchas_test 4000 --font "/home/afi/Android/Sdk/platforms/android-28/data/fonts/DancingScript-
Regular.ttf"

```
#### Train model to break the Claptcha Generated Captcha using Deep Learning(CNN)
```bash

python captcha_solver.py train --dest_train '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_train/' --dest_val '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_val/' --outdir '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha/model/' --batch_size 16 --lr 1e-3 --epochs 20 --n_classes 36 --shuffle True --dim '(40,100,1)'

```

#### Evaluate the model trained to break Captcha 

```bash

python captcha_solver.py evaluate --model_path /home/afi/gihtub/deep_learning_projects/CAPTHCAs/captcha/model/captcha_breaker.h5 --eval_dest '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha_test/' --outdir /home/afi/github/deep_learning_projects/CAPTCHAs/captcha/ --fetch_target True

```

#### Train a Model to generate Captchas similar to images in SVHN dataset using GANs

```bash


python captcha_gan.py train --dest_train '/home/afi/Downloads/train_32x32.mat' --outdir '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha/SVHN/' --dir_flag False --batch_size 100 --gen_input_dim 100 --gen_beta1 0.5 --gen_lr 0.0001 --dis_input_dim '(32,32,3)' --dis_lr 0.001 --dis_beta1 0.5 --alpha 0.2 --epochs 100 --smooth_coef 0.1

```

#### Generate Captchas using the trained Model

```bash

python captcha_gan.py generate-captcha --gen_input_dim 100 --num_images 200 --model_dir '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha/' --outdir '/home/afi/github/deep_learning_projects/CAPTCHAs/captcha/captcha_for_use/' --alpha 0.2

```

**These are sample commands and need to be changed accordingly based on data repositories,output directory,etc**













 






