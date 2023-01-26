<h3 align="center">Eukfinder</h3>

  <p align="center">
    project_description
    <br />
    <a href="https://github.com/dzhao2019/Share/wiki"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/dzhao2019/Share/wiki">View Demo</a>
    ·
    <a href="https://github.com/dzhao2019/Share/wiki">Report Bug</a>
    ·
    <a href="https://github.com/dzhao2019/Share/wiki">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project


<!-- GETTING STARTED -->
## Getting Started

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
  ```sh
  npm install npm@latest -g
  ```

### Installation


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

**Eukfinder read_prep**
usage: Eukfinder read_prep [-h] --r1 R1 --r2 R2 -n THREADS -i ILLUMINA_CLIP
                           --hcrop HCROP -l LEADING_TRIM -t TRAIL_TRIM --wsize
                           WSIZE --qscore QSCORE --mlen MLEN --hg HG -o
                           OUT_NAME --cdb CDB

optional arguments:
  -h, --help            show this help message and exit

Required arguments:
  Description

  --r1 R1, --reads-r1 R1    left reads
  
  --r2 R2, --reads-r2 R2    right reads
  
  -n THREADS, --threads THREADS     number of threads
                        
  -i ILLUMINA_CLIP, --illumina-clip ILLUMINA_CLIP     adaptor file
                        
  --hcrop HCROP, --head-crop HCROP    head trim
                        
  -l LEADING_TRIM, --leading-trim LEADING_TRIM    leading trim
                        
  -t TRAIL_TRIM, --trail-trim TRAIL_TRIM    trail trim
                        
  --wsize WSIZE, --window-size WSIZE    sliding window size
                        
  --qscore QSCORE, --quality-score QSCORE     quality score for trimming
                        
  --mlen MLEN, --min-length MLEN    minimum length
                        
  --hg HG, --host-genome HG     host genome to get map out
                        
  -o OUT_NAME, --out_name OUT_NAME    out name
                        
  --cdb CDB, --centrifuge-database CDB    path to centrifuge database
  
  
<!-- ROADMAP -->
## Roadmap

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!


<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

<!-- ACKNOWLEDGMENTS -->
## Acknowledgments


<p align="right">(<a href="#readme-top">back to top</a>)</p>