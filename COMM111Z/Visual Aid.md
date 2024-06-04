A visual aid helps enhance what the speaker is saying
* Adds another element to it by improving the message
* Gain attention and entertain the audience
	* Entertain
* Help explain and clarify
* Having a visual aid can be useful when explaining concepts
* Help elicit emotions to enhance what we are saying
* They help keep you organized
* **Always ask yourself:** What is the goal of this visual age, and it shouldn't be to fill speech time

Types of visual aids:
* Youtube overlays and backgrounds
* imbed video clips or hold objects
* Use multimedia
* Using a handout will distract people from your speech and people will start reading it and stop listening to you

Quote:
* It sucks when people read what is on the slide to you
	* Death by powerpoint
* Lists: 
	* Want to avoid a list and instead make them images and express things visually
	* Material items can also be visual aids

Charts:
* when you use a chart, take a minute and explain it to everyone because people will look at it and try to see what it means
* Charts can be used to tell stories
	* I can use a chart to start showing how AI is causing job loss
* Make sure your charts are appropriate for your audience
	* If it is too difficult to read highlight what you want them to see

Maps:
* Don't have maps that are too large, and it should highlight or focus on the area that you are talking about

Photos:
* Can be used to challenge, entertain, or even impact how they view the subject.
* Can use to connect it to you locally
* Challenges and ethics:
	* Be aware that photos can be doctored to try to manipulate the audience
	* What is actually in the photo and don't use one that is being manipulative
	* Beware of posing, people can make things look way different than they actually are

Guidlines:
* Enhance the speaker's message
* Content should be appropriate for the audience
* Images should be appropriate
* Visual aids should be used strategically
* Be creative with your visual aids



https://www.microsoft.com/en-us/worklab/work-trend-index/ai-at-work-is-here-now-comes-the-hard-part?ef_id=_k_Cj0KCQjw3ZayBhDRARIsAPWzx8rOfMPb-Ct3vphTFSusszrKDd348GskRjzq4B8CWrY09T-z41RtRF4aAo1uEALw_wcB_k_&OCID=AIDcmm9xzw3cn3_SEM__k_Cj0KCQjw3ZayBhDRARIsAPWzx8rOfMPb-Ct3vphTFSusszrKDd348GskRjzq4B8CWrY09T-z41RtRF4aAo1uEALw_wcB_k_&gad_source=1&gclid=Cj0KCQjw3ZayBhDRARIsAPWzx8rOfMPb-Ct3vphTFSusszrKDd348GskRjzq4B8CWrY09T-z41RtRF4aAo1uEALw_wcB

https://www.sciencedirect.com/science/article/pii/S2590051X23000308

```
#!/bin/bash
#SBATCH -J KH_P5_1 
#SBATCH -A cs475-575 
#SBATCH -p classgpufinal 
#SBATCH --constraint=v100 
#SBATCH --gres=gpu:1 
#SBATCH -o P_5_DGX_result.out 
#SBATCH -e P_5_DGX_result.err 
#SBATCH --mail-type=BEGIN,END,FAIL 
#SBATCH --mail-user=hernank9@oregonstate.edu

for t in 1024 4096 16384 65536 262144 1048576 2097152
do
        for b in 8 32 64 128 256
        do
                /usr/local/apps/cuda/11.7/bin/nvcc -DNUMTRIALS=$t -DBLOCKSIZE=$b -o proj05  proj05.cu
                ./proj05
        done
done

```

Hey, just a heads up, if you are running into an issue similar to this when trying to run your program 
```
In file included from /usr/local/apps/cuda/cuda-10.1/bin/../targets/x86_64-linux/include/cuda_runtime.h:83,
                 from <command-line>:
/usr/local/apps/cuda/cuda-10.1/bin/../targets/x86_64-linux/include/crt/host_config.h:138:2: error: #error -- unsupported GNU version! gcc versions later than 8 are not supported!
  138 | #error -- unsupported GNU version! gcc versions later than 8 are not supported!
      |  ^~~~~
```