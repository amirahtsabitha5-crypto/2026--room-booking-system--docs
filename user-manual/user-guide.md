# Room Booking System - User Guide

## Overview

Room Booking System adalah aplikasi untuk memudahkan pemesanan ruangan (meeting rooms, conference rooms, dll).

## Getting Started

### 1. Accessing the Application

- **Web**: Buka browser dan akses `http://localhost:5173` (development) atau URL produksi
- **Mobile**: Download aplikasi dari App Store (iOS) atau Google Play (Android)

## Main Features

### 1. View Available Rooms

1. Pada halaman utama, Anda akan melihat daftar semua ruangan yang tersedia
2. Setiap ruangan menampilkan:
   - Nama ruangan
   - Kapasitas
   - Lokasi
   - Fasilitas yang tersedia
   - Status ketersediaan

### 2. Book a Room

#### Web/Mobile
1. Klik tombol "Book Room" atau "+" untuk membuat pemesanan baru
2. Isi form berikut:
   - **Select Room**: Pilih ruangan yang ingin dipesannya
   - **Start Time**: Tentukan waktu mulai
   - **End Time**: Tentukan waktu selesai
   - **Purpose**: (optional) Tujuan pemesanan
3. Review detail booking Anda
4. Klik "Confirm Booking" untuk menyelesaikan

### 3. View Booking History

1. Navigasi ke "My Bookings" atau "Booking History"
2. Anda akan melihat semua booking Anda:
   - Booking aktif (upcoming)
   - Booking selesai (completed)
   - Booking dibatalkan (cancelled)

### 4. Manage Bookings

#### Edit Booking
1. Pilih booking dari daftar
2. Klik tombol "Edit"
3. Ubah waktu atau detail lainnya
4. Klik "Save Changes"

#### Cancel Booking
1. Pilih booking yang ingin dibatalkan
2. Klik tombol "Cancel"
3. Konfirmasi pembatalan

### 5. View Booking Status

Setiap booking memiliki status:
- **Pending**: Booking sedang menunggu konfirmasi
- **Confirmed**: Booking sudah dikonfirmasi
- **In Progress**: Waktu booking sedang berlangsung
- **Completed**: Booking telah selesai
- **Cancelled**: Booking dibatalkan

## Room Details

Ketika memilih ruangan, Anda akan melihat informasi:

- **Name**: Nama ruangan
- **Capacity**: Kapasitas maksimal orang
- **Location**: Lokasi ruangan (gedung, lantai)
- **Amenities**: Fasilitas yang tersedia
  - Projector
  - Whiteboard
  - WiFi
  - AC
  - dll

## Time Management

### Booking Requirements

- Booking minimum: 1 jam
- Booking maksimum: 8 jam
- Advance booking: Hingga 30 hari ke depan
- Pembatalan: Dapat dilakukan hingga 1 jam sebelum waktu booking

## Mobile App Features

### iOS
- Notifikasi upcoming bookings
- Offline viewing of booked rooms
- Calendar integration
- Siri shortcuts (coming soon)

### Android
- Notifikasi real-time
- Widget untuk quick booking
- Google Calendar sync
- Offline support

## Tips & Best Practices

1. **Book in Advance**: Pesan ruangan dengan waktu yang cukup
2. **Check Availability**: Lihat ketersediaan sebelum booking
3. **Update Booking**: Update waktu jika ada perubahan rencana
4. **Cancel Early**: Batalkan jika tidak akan membutuhkan ruangan
5. **Check Amenities**: Pastikan fasilitas yang dibutuhkan tersedia

## Troubleshooting

### Issue: Cannot Book Room

**Solution**:
- Pastikan waktu booking tidak bertabrakan dengan booking lain
- Cek apakah ruangan tersedia di waktu yang diinginkan
- Refresh halaman dan coba lagi

### Issue: Cannot Access App

**Solution**:
- Pastikan memiliki koneksi internet yang stabil
- Cek apakah aplikasi sudah diperbarui ke versi terbaru
- Restart aplikasi

### Issue: Booking Not Showing

**Solution**:
- Refresh halaman atau aplikasi
- Pastikan sudah login dengan akun yang benar
- Cek filter bookmark (upcoming, past, all)

## FAQ

**Q: Berapa lama saya bisa book ruangan?**
A: Anda bisa book ruangan hingga maksimal 8 jam per booking.

**Q: Bisa booking berapa jauh hari ke depan?**
A: Anda bisa booking hingga 30 hari ke depan.

**Q: Apa bisa mengubah booking setelah di-confirm?**
A: Ya, Anda bisa mengubah waktu atau ruangan selama tidak ada konflik dengan booking lain.

**Q: Apakah ada biaya untuk booking?**
A: Tidak ada biaya untuk booking ruangan di sistem ini.

**Q: Bagaimana kalau terlambat datang?**
A: Booking Anda tetap akan berlaku. Ruangan akan dianggap terisi sesaat setelah waktu mulai.

## Contact Support

Jika memiliki pertanyaan atau masalah:
- Email: support@roombooking.local
- Chat: Available dalam aplikasi
- Phone: +62-XXX-XXXX-XXXX

## Version History

- **v1.0.0** (Feb 2026): Initial Release
  - Basic room booking
  - View bookings
  - Cancel bookings
