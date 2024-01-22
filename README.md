import java.util.Scanner;
import java.util.ArrayList;

// Class abstrak sebagai blueprint untuk hewan
abstract class Hewan {
    private double berat;
    private double tinggi;
    private double panjang;

    // Constructor untuk inisialisasi data awal
    public Hewan(double berat, double tinggi, double panjang) {
        this.berat = berat;
        this.tinggi = tinggi;
        this.panjang = panjang;
    }

    // Abstract method untuk mendapatkan suara hewan
    public abstract String getSuara();

    // Getter untuk mendapatkan informasi hewan
    public String getInfo() {
        return "Berat: " + berat + " kg, Tinggi: " + tinggi + " cm, Panjang: " + panjang + " cm";
    }
}

// Class Kambing sebagai turunan dari Hewan
class Kambing extends Hewan {
    private int usia; // Usia kambing dalam bulan

    // Constructor untuk inisialisasi data awal
    public Kambing(double berat, double tinggi, double panjang, int usia) {
        super(berat, tinggi, panjang);
        this.usia = usia;
    }

    // Implementasi abstract method untuk mendapatkan suara kambing
    @Override
    public String getSuara() {
        return "Mbek mbek!";
    }

    // Getter untuk mendapatkan usia kambing
    public int getUsia() {
        return usia;
    }

    // Metode untuk memperbarui perkembangan kambing setiap bulan
    public void perkembanganBulanan() {
        usia++;
        // Tambahkan logika lain yang diinginkan untuk perkembangan bulanan
    }
}

// Class PedagangKambing untuk mendata perkembangan kambing-kambing yang dimiliki
class PedagangKambing {
    private ArrayList<Kambing> daftarKambing;

    // Constructor untuk inisialisasi data awal
    public PedagangKambing() {
        daftarKambing = new ArrayList<>();
    }

    // Metode untuk menambahkan kambing baru ke daftar
    public void beliKambing(double berat, double tinggi, double panjang) {
        Kambing kambingBaru = new Kambing(berat, tinggi, panjang, 0);
        daftarKambing.add(kambingBaru);
    }

    // Metode untuk menampilkan informasi setiap kambing dalam daftar
    public void tampilkanInformasiKambing() {
        System.out.println("Informasi Kambing:");
        for (Kambing kambing : daftarKambing) {
            System.out.println("Usia: " + kambing.getUsia() + " bulan");
            System.out.println(kambing.getInfo());
            System.out.println("Suara: " + kambing.getSuara());
            System.out.println();
        }
    }

    // Metode untuk melakukan perkembangan bulanan pada setiap kambing dalam daftar
    public void perkembanganBulanan() {
        for (Kambing kambing : daftarKambing) {
            kambing.perkembanganBulanan();
        }
    }
}

// Class Program sebagai entry point program
public class Program {
    public static void main(String[] args) {
        // Membuat objek PedagangKambing (Pak Slamet)
        PedagangKambing pakSlamet = new PedagangKambing();

        // Memasukkan data awal kambing
        pakSlamet.beliKambing(30.5, 80.0, 100.0);
        pakSlamet.beliKambing(25.0, 75.0, 90.0);

        // Menampilkan informasi kambing
        pakSlamet.tampilkanInformasiKambing();

        // Simulasi perkembangan bulanan
        for (int i = 1; i <= 12; i++) {
            System.out.println("\nPerkembangan Bulan ke-" + i + ":");
            pakSlamet.perkembanganBulanan();
            pakSlamet.tampilkanInformasiKambing();
        }
    }
}
