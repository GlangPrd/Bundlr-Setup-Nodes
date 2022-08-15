 # Sistem Gereksinimleri
 - Bellek: 8 GB RAM
 - CPU: 2 
 - Disk: 250 GB SSD 

 
 # Kurulum adımları:
 
 - wget -O NodeistBundlr.sh https://raw.githubusercontent.com/Nodeist/Kurulumlar/main/Bundlr/NodeistBundlr.sh && chmod +x NodeistBundlr.sh && ./NodeistBundlr.sh
 
 # Kurulum Sonrası Adımlar
 
 Arweave sitesine gidin ve bir cüzdan oluşturun: https://faucet.arweave.net/
 Siteyi açtığınızda bir ekran gelecek onay kutucuğunu işaretleyin ve Continue butonuna tıklayın.
 İkinci ekranda yine onay kutucuğunu işaretleyin ve Download Wallet butonuna tıklayın.
 Sonraki ekranda Open Tweet Pop-up butonuna tıklayın twit atmanız için bir pencere açılacak, cüzdan adresiniz orada yazıyor olacak. Cüzdan adresinizi kopyalayın. twit atmayın.
 Kopyaladığınız cüzdan adresini https://bundlr.network/faucet sitesine giderek yapıştırın. ardından bu siteden twit atın. Attığınız twitin linkini siteye gelip yapıştırın.
 Cüzdanımızı başarıyla bilgisayarımıza indirdik ve musluktan coin'imizi aldık.
 Şimdi yapmamız gereken şey indirdiğimiz cüzdan ismini düzenlemek.
 
 İndirdiğiniz dosyanın ismi şuna benzer: arweave-key-QeKJ_HaxE....................ejQ.json
 Bu dosyanın ismini wallet.json olarak güncelleyin. VE MUTLAKA YEDEKLEYİN
 Ardından bu cüzdanı sunucumuzda validator-rust klasörünün içine atıyoruz.
 
 #Servis dosyamızı oluşturuyoruz
 
-tee $HOME/validator-rust/.env > /dev/null <<EOF
PORT=80
BUNDLER_URL="https://testnet1.bundlr.network"
GW_CONTRACT="RkinCLBlY4L5GZFv8gCFcrygTyd5Xm91CzKlR6qxhKA"
GW_ARWEAVE="https://arweave.testnet1.bundlr.network"
EOF

Not : Kurulum yaklaşık 10 dakika sürüyor. bu yüzden bağlantı kesintilerine karşı önlem almak adına öncesinde screen oluşturmanız önerilir.

 Dockeri Başlat:
 
 - cd ~/validator-rust && docker-compose up -d
 
 Günlükleri Kontrol et:
 
 - cd ~/validator-rust && docker-compose logs --tail=100 -f
 
 Doğrulayıcıyı Başlatın:
 
 -npm i -g @bundlr-network/testnet-cli
 
 Doğrulayıcınızı ağa katın. ipadresiniz kısmını düzenleyin:
 
 - testnet-cli join RkinCLBlY4L5GZFv8gCFcrygTyd5Xm91CzKlR6qxhKA -w wallet.json -u "http://ipadresiniz:80" -s 25000000000000
 
 Done yazacak ve bitti.
 
 
  
