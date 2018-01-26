build:
	@docker build -t ysicing/caddy .
test:
	@docker run -d -p 2018:2015 --name caddy-test ysicing/caddy
run:
	@docker run -d -v $(pwd)/Caddyfile:/etc/Caddyfile -v $HOME/.caddy:/root/.caddy -p 80:80 -p 443:443 --name caddy ysicing/caddy
