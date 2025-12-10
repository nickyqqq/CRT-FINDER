# CRT-FINDER


a tool for auto finding extra subdomain from crt
and here is the ultimate recon method

1) get domains in the TXT file

2) use subfinder
subfinder -dL domains.txt -all -recursive -o  subdomains.txt

3) use my python CRT-FINDER tool for finding extra subdomain

4) merge the subdomain from crt finder to the old one
cat subdomains.txt /home/nicky/Desktop/crt.txt > subdomains2.txt

5) find alive subdomains by using httpx-toolkit
cat allsub.txt | httpx-toolkit -l allsub.txt -ports 443,80,8080,8000,8888 -threads 200 > alive_subdomains.txt

6) dirsearch
python dirsearch.py -l /home/nicky/Desktop/crypto/alive_subdomains.txt -x 500,502,429,404,400 -R 5 --random-agent -t 100 -F -o /home/nicky/Desktop/crypto/directory.txt

