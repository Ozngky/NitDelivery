# 🚚 NitDelivery

**Gelişmiş Minecraft Teslimat Sistemi Plugin'i**

[![Version](https://img.shields.io/badge/Version-1.0.0-brightgreen.svg)](https://github.com/Ozngky/NitDelivery)
[![Minecraft](https://img.shields.io/badge/Minecraft-1.20.1-blue.svg)](https://www.spigotmc.org/)
[![Java](https://img.shields.io/badge/Java-17%2B-orange.svg)](https://www.oracle.com/java/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://github.com/Ozngky/NitDelivery/blob/main/LICENSE)

## 📋 İçindekiler

- [Özellikler](#-özellikler)
- [Kurulum](#-kurulum)
- [Konfigürasyon](#-konfigürasyon)
- [Komutlar](#-komutlar)
- [İzinler](#-i̇zinler)
- [API Kullanımı](#-api-kullanımı)
- [Çoklu Sunucu Desteği](#-çoklu-sunucu-desteği)
- [Veritabanı](#-veritabanı)
- [Katkıda Bulunma](#-katkıda-bulunma)
- [Lisans](#-lisans)

## 🌟 Özellikler

### 🎯 Temel Özellikler
- **NPC Tabanlı Sistem**: Citizens plugin entegrasyonu ile teslimat NPC'leri
- **Minecraft Uyumlu Kategori Sistemi**: Bloklar, Madenler, Tarım, Yemekler kategorileri
- **Dinamik Kategori Yönetimi**: Oyun içinden kategori ekleme, silme ve düzenleme
- **Gerçek Zamanlı Teslimat**: Async işlemlerle optimum performans
- **Kapsamlı İstatistikler**: Detaylı oyuncu ve sunucu istatistikleri
- **Başarım Sistemi**: 6 farklı başarım seviyesi
- **Liderlik Tabloları**: Günlük, haftalık ve genel sıralamalar

### 🏢 Gelişmiş Özellikler
- **Çoklu Veritabanı Desteği**: SQLite ve MySQL desteği
- **Redis Cache**: Hızlı veri erişimi ve caching
- **RabbitMQ Entegrasyonu**: Güvenilir mesaj kuyruğu sistemi
- **Çoklu Sunucu Koordinasyonu**: Sunucular arası veri senkronizasyonu
- **Global Liderlik Tabloları**: Tüm sunucularda birleşik sıralama
- **Cross-Server Bildirimler**: Sunucular arası bildirim sistemi

### 🎨 Kullanıcı Deneyimi
- **Modern GUI**: İntuitive menü tasarımı
- **🌐 Çoklu Dil Desteği**: Türkçe (default) ve İngilizce dil desteği
- **Dinamik Dil Değişimi**: Config'ten dil ayarı değiştirilebilir
- **Sesli Geri Bildirim**: Aksiyon bazlı ses efektleri
- **Renkli Mesajlar**: Görsel olarak çekici mesaj sistemi
- **Responsive Tasarım**: Tüm ekran boyutlarına uygun

### ⚡ Performans & Güvenlik
- **Async Operations**: Non-blocking veritabanı işlemleri
- **Memory Efficient**: Optimize edilmiş bellek kullanımı
- **Error Handling**: Kapsamlı hata yönetimi
- **Data Validation**: Güvenli veri doğrulama
- **Auto Cleanup**: Otomatik veri temizliği

## 🚀 Kurulum

### Gereksinimler
- **Minecraft Server**: Spigot/Paper 1.20.1+
- **Java**: JDK 17 veya üzeri
- **Citizens Plugin**: v2.0.33+
- **RAM**: En az 2GB (çoklu sunucu için 4GB önerilir)

### Adım Adım Kurulum

1. **Plugin Dosyasını İndirin**
   ```bash
   wget https://github.com/Ozngky/NitDelivery/releases/latest/download/NitDelivery.jar
   ```

2. **Plugins Klasörüne Yerleştirin**
   ```bash
   cp NitDelivery.jar /path/to/server/plugins/
   ```

3. **Citizens Plugin'ini Kurun** (henüz kurulmamışsa)
   ```bash
   # Citizens plugin'ini SpigotMC'den indirin
   ```

4. **Sunucuyu Başlatın**
   ```bash
   java -jar server.jar
   ```

5. **Konfigürasyonu Ayarlayın**
   - `plugins/NitDelivery/config.yml` dosyasını düzenleyin
   - Veritabanı ayarlarını yapılandırın
   - Çoklu sunucu desteği için Redis/RabbitMQ ayarlayın

## ⚙️ Konfigürasyon

### Temel Konfigürasyon (config.yml)

```yaml
# Veritabanı Ayarları
database:
  type: "sqlite"  # sqlite veya mysql
  host: "localhost"
  port: 3306
  name: "nitdelivery"
  username: "root"
  password: ""

# Çoklu Sunucu Desteği
multi-server:
  enabled: false
  server-id: "server1"
  server-name: "NitDelivery Server"

# Redis Ayarları
redis:
  enabled: false
  host: "localhost"
  port: 6379
  password: ""

# RabbitMQ Ayarları
rabbitmq:
  enabled: false
  host: "localhost"
  port: 5672
  username: "guest"
  password: "guest"
```

### Gelişmiş Ayarlar

```yaml
# Ekonomi Sistemi
economy:
  enabled: true
  base-reward: 100.0
  bonus-multiplier: 1.5

# Performans Ayarları
performance:
  async-operations: true
  cache-timeout: 300
  cleanup-interval: 1800
```

## 🎮 Komutlar

### Oyuncu Komutları

| Komut | Açıklama | Kullanım |
|-------|----------|----------|
| `/nitdelivery stats` | İstatistiklerinizi görüntüler | `/nitdelivery stats [oyuncu]` |
| `/nitdelivery top` | Liderlik tablosunu gösterir | `/nitdelivery top [kategori]` |
| `/nitdelivery help` | Yardım menüsünü açar | `/nitdelivery help` |

### Admin Komutları

| Komut | Açıklama | Kullanım |
|-------|----------|----------|
| `/teslimatolustur` | Teslimat NPC'si oluşturur | `/teslimatolustur` |
| `/nitdelivery reload` | Plugin'i yeniden yükler | `/nitdelivery reload` |
| `/nitdelivery reset` | İstatistikleri sıfırlar | `/nitdelivery reset [oyuncu]` |
| `/nitdelivery info` | Plugin bilgilerini gösterir | `/nitdelivery info` |
| `/nitdelivery category` | Kategori yönetimi | `/nitdelivery category <komut>` |

### Kategori Yönetimi Komutları

| Komut | Açıklama | Kullanım |
|-------|----------|----------|
| `/nitdelivery category list` | Kategorileri listeler | `/nitdelivery category list` |
| `/nitdelivery category add` | Yeni kategori ekler | `/nitdelivery category add <id> <isim> <açıklama> <materyal> <slot>` |
| `/nitdelivery category remove` | Kategori siler | `/nitdelivery category remove <id>` |
| `/nitdelivery category edit` | Kategori düzenler | `/nitdelivery category edit <id> <özellik> <değer>` |
| `/nitdelivery category setslot` | Kategori slotunu değiştirir | `/nitdelivery category setslot <id> <slot>` |
| `/nitdelivery category toggle` | Kategori durumunu değiştirir | `/nitdelivery category toggle <id>` |

#### Kategori Yönetimi Örnekleri

```bash
# Yeni kategori ekleme
/nitdelivery category add weapons "Silahlar" "Savaş aletleri" IRON_SWORD 14

# Kategori ismini değiştirme
/nitdelivery category edit weapons name "Savaş Aletleri"

# Kategori slotunu değiştirme
/nitdelivery category setslot weapons 15

# Kategori durumunu değiştirme (aktif/pasif)
/nitdelivery category toggle weapons

# Kategori silme
/nitdelivery category remove weapons
```

#### Düzenlenebilir Kategori Özellikleri
- **name**: Kategori görünen ismi
- **description**: Kategori açıklaması
- **icon**: Kategori ikonu (Minecraft materyal ismi)

### Varsayılan Minecraft Kategorileri

| Kategori | Açıklama | Slot | Ürünler |
|----------|----------|------|---------|
| **Bloklar** | İnşaat için bloklar | 10 | Ahşap, Taş, Cam, Yün |
| **Madenler** | Değerli madenler | 11 | Demir, Altın, Elmas, Zümrüt |
| **Tarım** | Tarım ürünleri | 12 | Buğday, Havuç, Patates, Pancar |
| **Yemekler** | Lezzetli yemekler | 13 | Ekmek, Biftek, Balık, Pasta |

## 🔐 İzinler

### Temel İzinler

```yaml
nitdelivery.use:
  description: Temel plugin kullanımı
  default: true

nitdelivery.npc.interact:
  description: NPC ile etkileşim
  default: true

nitdelivery.order.create:
  description: Sipariş oluşturma
  default: true
```

### Admin İzinleri

```yaml
nitdelivery.admin:
  description: Tüm admin komutları
  default: op

nitdelivery.npc.create:
  description: NPC oluşturma
  default: op

nitdelivery.reload:
  description: Plugin yeniden yükleme
  default: op

nitdelivery.reset:
  description: İstatistik sıfırlama
  default: op

nitdelivery.category.manage:
  description: Kategori yönetimi
  default: op

nitdelivery.category.add:
  description: Kategori ekleme
  default: op

nitdelivery.category.remove:
  description: Kategori silme
  default: op

nitdelivery.category.edit:
  description: Kategori düzenleme
  default: op

nitdelivery.category.list:
  description: Kategori listesini görme
  default: op

nitdelivery.category.toggle:
  description: Kategori durumunu değiştirme
  default: op
```

### Çoklu Sunucu İzinleri

```yaml
nitdelivery.multiserver.manage:
  description: Çoklu sunucu yönetimi
  default: op

nitdelivery.global.stats:
  description: Global istatistikleri görme
  default: true
```

## 💻 API Kullanımı

### Maven Dependency

```xml
<dependency>
    <groupId>com.ozngky</groupId>
    <artifactId>NitDelivery</artifactId>
    <version>1.0.0</version>
    <scope>provided</scope>
</dependency>
```

**GitHub Repository**: https://github.com/Ozngky/NitDelivery

### Temel API Kullanımı

```java
public class MyPlugin extends JavaPlugin {
    
    private NitDelivery nitDelivery;
    
    @Override
    public void onEnable() {
        // NitDelivery instance'ını alın
        nitDelivery = (NitDelivery) getServer().getPluginManager().getPlugin("NitDelivery");
        
        // Player stats'ları alın
        PlayerStats stats = nitDelivery.getPlayerStatsManager()
            .getPlayerStats(player.getUniqueId());
        
        // Kategori yönetimi
        CategoryManager categoryManager = nitDelivery.getCategoryManager();
        
        // Yeni kategori oluşturun
        boolean success = categoryManager.createCategory(
            "weapons", 
            "Silahlar", 
            "Savaş aletleri", 
            Material.IRON_SWORD, 
            14
        );
        
        // Kategori listesini alın
        List<Category> categories = categoryManager.getEnabledCategories();
        
        // Belirli kategoriyi alın
        Category weaponsCategory = categoryManager.getCategory("weapons");
        
        // Kategori ürünlerini alın
        List<Product> weapons = categoryManager.getEnabledProducts("weapons");
        
        // Yeni sipariş oluşturun
        Product product = categoryManager.getProduct("food", "burger");
        
        boolean orderSuccess = nitDelivery.getDeliveryManager()
            .createOrder(player, product);
    }
}
```

### Kategori Yönetimi API

```java
public class CategoryAPI {
    
    private CategoryManager categoryManager;
    
    public void manageCategoriesExample() {
        // Kategori oluşturma
        boolean created = categoryManager.createCategory(
            "tools",           // Kategori ID
            "Aletler",         // Kategori ismi
            "Kullanışlı aletler", // Açıklama
            Material.DIAMOND_PICKAXE, // İkon
            16                 // Slot
        );
        
        // Kategori güncelleme
        categoryManager.updateCategoryName("tools", "Maden Aletleri");
        categoryManager.updateCategoryDescription("tools", "Maden çıkarma aletleri");
        categoryManager.updateCategoryIcon("tools", Material.IRON_PICKAXE);
        categoryManager.updateCategorySlot("tools", 17);
        
        // Kategori durumunu değiştirme
        categoryManager.toggleCategoryEnabled("tools");
        
        // Kategori silme
        categoryManager.deleteCategory("tools");
        
        // Kategori sorgulama
        boolean exists = categoryManager.categoryExists("tools");
        boolean slotTaken = categoryManager.isSlotTaken(16);
        int nextSlot = categoryManager.getNextAvailableSlot();
        
        // Kategorileri listeleme
        List<String> categoryIds = categoryManager.getCategoryIds();
        List<Category> allCategories = categoryManager.getAllCategories();
        List<Category> enabledCategories = categoryManager.getEnabledCategories();
    }
}
```

### Event API

```java
@EventHandler
public void onDeliveryComplete(DeliveryCompleteEvent event) {
    Player player = event.getPlayer();
    Product product = event.getProduct();
    double reward = event.getReward();
    
    // Custom logic burada
}

@EventHandler
public void onCategoryCreate(CategoryCreateEvent event) {
    Category category = event.getCategory();
    CommandSender creator = event.getCreator();
    
    // Kategori oluşturma eventi
}

@EventHandler
public void onCategoryDelete(CategoryDeleteEvent event) {
    String categoryId = event.getCategoryId();
    CommandSender deleter = event.getDeleter();
    
    // Kategori silme eventi
}
```

## 🌐 Çoklu Sunucu Desteği

### Redis Konfigürasyonu

```yaml
redis:
  enabled: true
  host: "redis.example.com"
  port: 6379
  password: "secure_password"
  database: 0
```

### RabbitMQ Konfigürasyonu

```yaml
rabbitmq:
  enabled: true
  host: "rabbitmq.example.com"
  port: 5672
  username: "nitdelivery"
  password: "secure_password"
  virtual-host: "/nitdelivery"
```

### Çoklu Sunucu Özellikleri

- **Global Liderlik Tabloları**: Tüm sunuculardaki oyuncuları içeren sıralamalar
- **Cross-Server Bildirimler**: Sunucular arası başarım ve teslimat bildirimleri
- **Data Synchronization**: Gerçek zamanlı veri senkronizasyonu
- **Load Balancing**: Akıllı yük dağıtımı
- **Failover Support**: Sunucu arızalarında otomatik geçiş

## 🌍 Çoklu Dil Desteği

### Desteklenen Diller

- **🇹🇷 Türkçe (tr)**: Varsayılan dil
- **🇺🇸 İngilizce (en)**: Tam destek

### Dil Ayarları

```yaml
# config.yml
general:
  language: "tr"  # tr (Türkçe) veya en (İngilizce)
```

### Özelleştirme

```yaml
# messages.yml
tr:
  general:
    prefix: "&6[NitDelivery] &f"
    no-permission: "&cBu komutu kullanma izniniz yok!"
    reload-success: "&aPlugin başarıyla yeniden yüklendi!"

en:
  general:
    prefix: "&6[NitDelivery] &f"
    no-permission: "&cYou don't have permission to use this command!"
    reload-success: "&aPlugin successfully reloaded!"
```

### Dil Sistemi Özellikleri

- **Dinamik Dil Değişimi**: Config'ten dil değiştirilebilir
- **Fallback Desteği**: Eksik çeviriler için otomatik fallback
- **Placeholder Desteği**: Tüm mesajlarda placeholder kullanımı
- **Geriye Uyumluluk**: Eski message format'ı ile uyumlu
- **Kolay Genişletme**: Yeni diller kolayca eklenebilir

### Yeni Dil Ekleme

1. **messages.yml**'de yeni dil kodu ekleyin:
```yaml
de:  # Almanca için
  general:
    prefix: "&6[NitDelivery] &f"
    # Diğer mesajlar...
```

2. **ConfigManager**'da dil desteğini ekleyin:
```java
public boolean isLanguageSupported(String language) {
    return language.equals("tr") || language.equals("en") || language.equals("de");
}
```

3. **config.yml**'de dil ayarını güncelleyin:
```yaml
general:
  language: "de"
```

## 🗄️ Veritabanı

### SQLite (Varsayılan)
- Kolay kurulum
- Dosya tabanlı
- Küçük-orta sunucular için ideal

### MySQL (Önerilen - Büyük Sunucular)
- Yüksek performans
- Çoklu sunucu desteği
- Gelişmiş sorgu optimizasyonu

### Veritabanı Şeması

```sql
-- Player Statistics
CREATE TABLE player_stats (
    player_uuid VARCHAR(36) PRIMARY KEY,
    player_name VARCHAR(16),
    total_deliveries INT DEFAULT 0,
    total_earnings DOUBLE DEFAULT 0,
    today_deliveries INT DEFAULT 0,
    last_delivery_time BIGINT DEFAULT 0,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
    updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
);

-- Delivery Orders
CREATE TABLE delivery_orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    player_uuid VARCHAR(36),
    product_name VARCHAR(255),
    product_category VARCHAR(100),
    order_time BIGINT,
    delivery_time BIGINT,
    reward_amount DOUBLE,
    status VARCHAR(50),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

-- Server Statistics (Multi-server)
CREATE TABLE server_stats (
    server_id VARCHAR(100) PRIMARY KEY,
    server_name VARCHAR(255),
    total_deliveries INT DEFAULT 0,
    total_earnings DOUBLE DEFAULT 0,
    active_players INT DEFAULT 0,
    last_update BIGINT DEFAULT 0
);
```

## 📊 İstatistikler ve Metrikler

### Oyuncu İstatistikleri
- **Toplam Teslimatlar**: Tüm zamanların teslimat sayısı
- **Toplam Kazançlar**: Elde edilen toplam para
- **Günlük Teslimatlar**: Bugün yapılan teslimat sayısı
- **Son Teslimat Zamanı**: En son teslimat tarihi
- **Başarımlar**: Açılan başarım rozetleri
- **Sıralama**: Liderlik tablosundaki konum

### Sunucu İstatistikleri
- **Aktif Oyuncular**: Anlık çevrimiçi oyuncu sayısı
- **Toplam Siparişler**: Sistemdeki aktif sipariş sayısı
- **Günlük İstatistikler**: Günlük toplam teslimat ve kazanç
- **Performans Metrikleri**: CPU ve bellek kullanımı

## 🏆 Başarım Sistemi

| Başarım | Gereksinim | Ödül |
|---------|-----------|------|
| **İlk Teslimat** | 1 teslimat | 🥉 Bronz rozet |
| **Teslimat Uzmanı** | 10 teslimat | 🥈 Gümüş rozet |
| **Teslimat Profesyoneli** | 50 teslimat | 🥇 Altın rozet |
| **Teslimat Efendisi** | 100 teslimat | 💎 Elmas rozet |
| **Teslimat Efsanesi** | 500 teslimat | 🌟 Yıldız rozet |
| **Teslimat Tanrısı** | 1000 teslimat | 👑 Kraliyet rozeti |

## 🔧 Geliştirici Rehberi

### Proje Yapısı

```
src/main/java/com/ozngky/nitdelivery/
├── commands/           # Komut işleyicileri
│   ├── DeliveryCommand.java        # Ana komut (kategori yönetimi dahil)
│   └── TeslimatolusturCommand.java # NPC oluşturma
├── listeners/          # Event listener'ları
├── managers/           # Core yönetici sınıfları
│   ├── CategoryManager.java        # Kategori yönetimi (YENİ)
│   ├── ConfigManager.java          # Konfigürasyon
│   ├── DatabaseManager.java        # Veritabanı
│   ├── DeliveryManager.java        # Teslimat sistemi
│   └── ...
├── models/             # Veri modelleri
│   ├── Category.java               # Kategori modeli (YENİ)
│   ├── Product.java                # Ürün modeli
│   └── ...
├── utils/              # Yardımcı araçlar
└── NitDelivery.java    # Ana plugin sınıfı
```

### Build İşlemi

```bash
# Projeyi klonlayın
git clone https://github.com/Ozngky/NitDelivery.git
cd NitDelivery

# Maven ile build edin
mvn clean package

# JAR dosyası target/ klasöründe oluşacak
```

### Testing

```bash
# Unit testleri çalıştırın
mvn test

# Integration testleri
mvn integration-test
```

## 🐛 Hata Raporlama

Hata bulduğunuzda lütfen aşağıdaki bilgileri ile birlikte [GitHub Issues](https://github.com/Ozngky/NitDelivery/issues) sayfasında bildirin:

- **Minecraft Versiyonu**
- **Plugin Versiyonu**
- **Server Software** (Spigot/Paper)
- **Hata Mesajı** (tam log)
- **Tekrar Etme Adımları**

## 📈 Performans Optimizasyonu

### Önerilen Ayarlar

```yaml
# Büyük sunucular için
performance:
  async-operations: true
  cache-timeout: 600      # 10 dakika
  cleanup-interval: 3600  # 1 saat

# Redis cache (çoklu sunucu)
redis:
  enabled: true
  # Connection pooling
  max-connections: 50
  timeout: 5000
```

### JVM Optimizasyonu

```bash
# Server başlatma parametreleri
java -Xms4G -Xmx8G -XX:+UseG1GC -XX:+ParallelRefProcEnabled \
     -XX:MaxGCPauseMillis=200 -XX:+UnlockExperimentalVMOptions \
     -XX:+DisableExplicitGC -jar server.jar
```

## 🔄 Güncelleme Notları

### v1.0.0 (Current)
- ✅ İlk stable release
- ✅ Çoklu sunucu desteği
- ✅ Redis & RabbitMQ entegrasyonu
- ✅ MySQL & SQLite desteği
- ✅ Kapsamlı API
- ✅ Minecraft uyumlu kategori sistemi
- ✅ Dinamik kategori yönetimi
- ✅ Oyun içi kategori komutları
- ✅ Çoklu dil desteği (TR/EN)

### Gelecek Güncellemeler
- 🔄 **v1.1.0**: Vault ekonomi entegrasyonu
- 🔄 **v1.2.0**: PlaceholderAPI desteği
- 🔄 **v1.3.0**: Web dashboard
- 🔄 **v1.4.0**: Mobile app entegrasyonu

## 🤝 Katkıda Bulunma

Projeye katkıda bulunmak istiyorsanız:

1. **Fork** edin
2. **Feature branch** oluşturun (`git checkout -b feature/amazing-feature`)
3. **Commit** edin (`git commit -m 'Add amazing feature'`)
4. **Push** edin (`git push origin feature/amazing-feature`)
5. **Pull Request** açın

### Katkı Kuralları
- Clean code prensiplerine uyun
- Javadoc yorumları ekleyin
- Unit testler yazın
- Commit mesajlarını anlamlı yapın

## 📝 Lisans

Bu proje MIT lisansı altında lisanslanmıştır. Detaylar için [LICENSE](https://github.com/Ozngky/NitDelivery/blob/main/LICENSE) dosyasına bakın.

## 👥 İletişim ve Destek

- **GitHub**: [@Ozngky](https://github.com/Ozngky)
- **Discord**: `Ozngky`
- **Email**: [mail@bloknit.com](mailto:mail@bloknit.com)
- **Website**: [https://bloknit.com](https://bloknit.com)

### Proje Linkleri
- **Repository**: [NitDelivery](https://github.com/Ozngky/NitDelivery)
- **Issues**: [Bug Report & Feature Request](https://github.com/Ozngky/NitDelivery/issues)
- **Releases**: [Latest Downloads](https://github.com/Ozngky/NitDelivery/releases)

### Destek Kanalları
- 📋 **GitHub Issues**: [Bug report ve feature request](https://github.com/Ozngky/NitDelivery/issues)
- 📖 **GitHub Wiki**: [Detaylı dokümantasyon](https://github.com/Ozngky/NitDelivery/wiki)
- 🔄 **GitHub Discussions**: [Topluluk tartışmaları](https://github.com/Ozngky/NitDelivery/discussions)
- 📦 **GitHub Releases**: [Güncel sürümler](https://github.com/Ozngky/NitDelivery/releases)

## 🙏 Teşekkürler

- **Citizens Team**: Harika NPC plugin'i için
- **Spigot/Paper Teams**: Güçlü server platformu için
- **Community**: Geri bildirimler ve katkılar için

---

**NitDelivery** ile sunucunuzda profesyonel teslimat sistemi kurun! 🚚✨

---

*Made with ❤️ by [Ozngky](https://bloknit.com) - Visit [bloknit.com](https://bloknit.com) for more projects* 