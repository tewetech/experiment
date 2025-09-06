#!/bin/bash


# Fungsi untuk menampilkan menu utama
show_menu() {
    echo "=========================================="
    echo "    GitHub README Generator 🤖"
    echo "=========================================="
    echo "Pilih opsi untuk README Anda:"
    echo "1. Tambah judul utama"
    echo "2. Tambah deskripsi proyek"
    echo "3. Tambah badge (misalnya, status build, lisensi)"
    echo "4. Tambah bagian 'Fitur'"
    echo "5. Tambah bagian 'Cara Menginstal'"
    echo "6. Tambah bagian 'Penggunaan'"
    echo "7. Tambah bagian 'Kontribusi'"
    echo "8. Tambah bagian 'Lisensi'"
    echo "9. Pratinjau README.md"
    echo "10. Selesai & simpan README.md"
    echo "11. Keluar tanpa menyimpan"
    echo "=========================================="
    read -p "Masukkan pilihan Anda (1-11): " choice
}


# Fungsi untuk menambahkan judul
add_title() {
    read -p "Masukkan judul utama proyek: " title
    echo "# $title" >> README.md
    echo "Judul berhasil ditambahkan. ✅"
}


# Fungsi untuk menambahkan deskripsi
add_description() {
    read -p "Masukkan deskripsi singkat proyek: " desc
    echo "" >> README.md
    echo "$desc" >> README.md
    echo "Deskripsi berhasil ditambahkan. ✅"
}


# Fungsi untuk menambahkan badge
add_badge() {
    echo "Pilih jenis badge yang ingin ditambahkan:"
    echo "1. Lisensi"
    echo "2. Status Build (dari GitHub Actions)"
    echo "3. Lainnya (masukkan URL manual)"
    read -p "Pilihan Anda: " badge_choice


    case $badge_choice in
        1)
            read -p "Masukkan nama lisensi (misalnya, MIT, Apache-2.0): " license_name
            badge_url="https://img.shields.io/badge/Lisensi-$license_name-blue.svg"
            link_url="https://opensource.org/licenses/$license_name"
            ;;
        2)
            read -p "Masukkan nama user/repo (misalnya, username/repo-name): " repo_name
            badge_url="https://github.com/$repo_name/actions/workflows/main.yml/badge.svg"
            link_url="https://github.com/$repo_name/actions/workflows/main.yml"
            ;;
        3)
            read -p "Masukkan URL badge (gambar): " badge_url
            read -p "Masukkan URL tautan badge: " link_url
            ;;
        *)
            echo "Pilihan tidak valid."
            return
            ;;
    esac
    echo "[![]($badge_url)]($link_url)" >> README.md
    echo "Badge berhasil ditambahkan. ✅"
}


# Fungsi untuk menambahkan bagian dengan header
add_section() {
    read -p "Masukkan judul bagian (misalnya, Fitur, Instalasi, Penggunaan): " section_title
    echo "" >> README.md
    echo "---" >> README.md
    echo "## $section_title" >> README.md
    read -p "Sekarang, masukkan konten untuk bagian '$section_title'. Tekan ENTER untuk baris baru, lalu ketik 'END' pada baris baru dan tekan ENTER lagi saat selesai."
    while IFS= read -r line
    do
        if [[ "$line" == "END" ]]; then
            break
        fi
        echo "$line" >> README.md
    done
    echo "Bagian '$section_title' berhasil ditambahkan. ✅"
}


# Loop utama program
while true
do
    show_menu


    case $choice in
        1)
            add_title
            ;;
        2)
            add_description
            ;;
        3)
            add_badge
            ;;
        4|5|6|7|8)
            add_section
            ;;
        9)
            echo ""
            echo "=========================================="
            echo "        Pratinjau README.md"
            echo "=========================================="
            cat README.md
            echo "=========================================="
            ;;
        10)
            echo "Selesai! File README.md Anda telah dibuat. ✨"
            break
            ;;
        11)
            rm README.md 2> /dev/null
            echo "Keluar. File tidak disimpan. 🚮"
            exit 0
            ;;
        *)
            echo "Pilihan tidak valid. Silakan coba lagi."
            ;;
    esac
    echo ""
done
