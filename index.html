<?php
session_start();
$conn = mysqli_connect("localhost","root","","ukk_pengaduan");
if(!$conn) die("Koneksi gagal");

function q($s){ 
    global $conn; 
    return mysqli_query($conn,$s); 
}

$page = isset($_GET['page']) ? $_GET['page'] : 'login';
$msg  = "";


if(isset($_POST['register'])){
  $nis = mysqli_real_escape_string($conn, $_POST['nis']); 
  $kelas = mysqli_real_escape_string($conn, $_POST['kelas']);

  $c = q("SELECT * FROM siswa WHERE nis='$nis'");
  if(mysqli_num_rows($c) > 0) {
      $msg = "NIS sudah terdaftar!";
  } else {
      // Perbaikan: Sebutkan nama kolom secara spesifik (nis, kelas)
      $insert = q("INSERT INTO siswa (nis, kelas) VALUES ('$nis', '$kelas')");
      
      if($insert) {
          $msg = "Data siswa berhasil ditambahkan.";
          // Perbaikan: Jika yang menambah adalah Admin, jangan redirect ke login
          if(!isset($_SESSION['role']) || $_SESSION['role'] != 'admin') {
              header("Location:index.php?page=login"); 
              exit; 
          }
      } else {
          $msg = "Gagal menambah data: " . mysqli_error($conn);
      }
  }
}

if(isset($_POST['login'])){
  $u=$_POST['username']; $p=$_POST['password'];
  $a=q("SELECT * FROM admin WHERE username='$u' AND password='$p'");
  if(mysqli_num_rows($a)>0){
    $_SESSION['role']="admin"; $_SESSION['user']=$u;
    header("Location:index.php?page=aspirasi"); exit;
  }
  $s=q("SELECT * FROM siswa WHERE nis='$u' AND kelas='$p'");
  if(mysqli_num_rows($s)>0){
    $_SESSION['role']="siswa"; $_SESSION['user']=$u;
    header("Location:index.php?page=form"); exit;
  }
  $msg="Login gagal! Periksa username/password.";
}

if($page=="logout"){ 
    session_destroy(); 
    header("Location:index.php?page=login"); 
    exit; 
}


if(isset($_POST['add_admin'])){
    $u = $_POST['username']; $p = $_POST['password'];
    $cek = q("SELECT * FROM admin WHERE username='$u'");
    if(mysqli_num_rows($cek) > 0){
        $msg = "Username Admin sudah digunakan!";
    } else {
        q("INSERT INTO admin (username, password) VALUES ('$u', '$p')");
        $msg = "Admin baru berhasil ditambahkan!";
    }
}

if(isset($_POST['edit_admin'])) {
    q("UPDATE admin SET password='$_POST[password]' WHERE id_admin='$_POST[id_admin]'");
    $msg = "Password admin diperbarui!";
}

if(isset($_GET['del_admin'])) q("DELETE FROM admin WHERE id_admin='$_GET[del_admin]'");


if(isset($_POST['add_kat'])) q("INSERT INTO kategori VALUES(NULL,'$_POST[nama]')");
if(isset($_GET['del_kat'])) q("DELETE FROM kategori WHERE id_kategori='$_GET[del_kat]'");


if(isset($_POST['edit_siswa'])) q("UPDATE siswa SET kelas='$_POST[kelas]' WHERE nis='$_POST[nis]'");
if(isset($_GET['del_siswa'])) q("DELETE FROM siswa WHERE nis='$_GET[del_siswa]'");


if(isset($_POST['kirim'])){
  $tgl_skrg = date("Y-m-d H:i:s");
  q("INSERT INTO input_aspirasi (nis, id_kategori, lokasi, ket, waktu) VALUES ('$_SESSION[user]', '$_POST[id_kategori]', '$_POST[lokasi]', '$_POST[ket]', '$tgl_skrg')");
  $msg = "Aspirasi berhasil dikirim!";
}


if(isset($_POST['proses'])){
  $id=$_POST['id_pelaporan']; $st=$_POST['status']; $fb=$_POST['feedback'];
  $c=q("SELECT * FROM aspirasi WHERE id_pelaporan='$id'");
  if(mysqli_num_rows($c) > 0) {
    q("UPDATE aspirasi SET status='$st', feedback='$fb' WHERE id_pelaporan='$id'");
  } else {
    $res_ia = q("SELECT id_kategori FROM input_aspirasi WHERE id_pelaporan='$id'");
    $data_ia = mysqli_fetch_assoc($res_ia);
    $kat = $data_ia['id_kategori'];
    q("INSERT INTO aspirasi (id_pelaporan, id_kategori, status, feedback) VALUES ('$id', '$kat', '$st', '$fb')");
  }
  $msg = "Tanggapan diperbarui!";
}
?>

<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Aspirasi Pengaduan Sarana Sekolah</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        body { background-color: #f8f9fa; }
        .card { border: none; box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
    </style>
</head>
<body>

<nav class="navbar navbar-expand-lg navbar-dark bg-primary mb-4">
    <div class="container">
        <a class="navbar-brand fw-bold" href="#">ASPIRASI</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav me-auto">
                <?php if(!isset($_SESSION['role'])): ?>
                    <li class="nav-item"><a class="nav-link" href="?page=login">Login</a></li>
                    <li class="nav-item"><a class="nav-link" href="?page=register">Daftar Siswa</a></li>
                <?php else: ?>
                    <?php if($_SESSION['role']=="siswa"): ?>
                        <li class="nav-item"><a class="nav-link" href="?page=form">Input Aspirasi</a></li>
                        <li class="nav-item"><a class="nav-link" href="?page=histori">Histori Aspirasi</a></li>
                    <?php else: ?>
                        <li class="nav-item"><a class="nav-link" href="?page=aspirasi">Laporan Aspirasi</a></li>
                        <li class="nav-item"><a class="nav-link" href="?page=kategori">Kategori</a></li>
                        <li class="nav-item"><a class="nav-link" href="?page=siswa">Data Siswa</a></li>
                        <li class="nav-item"><a class="nav-link" href="?page=user_admin">Data Admin</a></li>
                    <?php endif; ?>
                <?php endif; ?>
            </ul>
            <?php if(isset($_SESSION['role'])): ?>
                <div class="d-flex align-items-center text-white">
                    <span class="me-3 small">Halo, <b><?= $_SESSION['user'] ?></b></span>
                    <a href="?page=logout" class="btn btn-danger btn-sm">Logout</a>
                </div>
            <?php endif; ?>
        </div>
    </div>
</nav>

<div class="container">
    <?php if($msg != ""): ?>
        <div class="alert alert-primary alert-dismissible fade show" role="alert">
            <?= $msg ?>
            <button type="button" class="btn-close" data-bs-dismiss="alert"></button>
        </div>
    <?php endif; ?>

    <?php if(!isset($_SESSION['role'])){ ?>
        <div class="row justify-content-center mt-5">
            <div class="col-md-4">
                <div class="card p-4 text-center">
                    <?php if($page=="register"){ ?>
                        <h4 class="mb-3">Daftar Siswa</h4>
                        <form method="post">
                            <input name="nis" class="form-control mb-2" placeholder="Masukkan NIS" required>
                            <input name="kelas" class="form-control mb-3" placeholder="Masukkan Kelas/Password" required>
                            <button name="register" class="btn btn-primary w-100">Daftar Sekarang</button>
                        </form>
                    <?php } else { ?>
                        <h4 class="mb-3">Login User</h4>
                        <form method="post">
                            <input name="username" class="form-control mb-2" placeholder="Username / NIS" required>
                            <input name="password" type="password" class="form-control mb-3" placeholder="Kelas/Password" required>
                            <button name="login" class="btn btn-primary w-100">Masuk</button>
                        </form>
                    <?php } ?>
                </div>
            </div>
        </div>
    <?php } else { ?>

        <?php if($_SESSION['role']=="siswa"){ ?>
            <?php if($page=="form"){ ?>
                <div class="card p-4 shadow-sm">
                    <h3>Kirim Aspirasi Baru</h3>
                    <form method="post">
                        <div class="mb-3">
                            <label class="form-label">Pilih Kategori</label>
                            <select name="id_kategori" class="form-select">
                                <?php 
                                $k=q("SELECT * FROM kategori"); 
                                while($r=mysqli_fetch_assoc($k)) 
                                echo "<option value='$r[id_kategori]'>$r[ket_kategori]</option>"; 
                                ?>
                            </select>
                        </div>
                        <div class="mb-3">
                            <input name="lokasi" class="form-control" placeholder="Lokasi (Contoh: Kantin, Lab Komp)" required>
                        </div>
                        <div class="mb-3">
                            <textarea name="ket" class="form-control" placeholder="Jelaskan secara detail..." rows="4" required></textarea>
                        </div>
                        <button name="kirim" class="btn btn-success px-4">Kirim Laporan</button>
                    </form>
                </div>
            <?php } ?>

            <?php if($page=="histori"){ ?>
                <div class="card p-4">
                    <h3 class="mb-4 text-primary">Status Laporan Aspirasi</h3>
   <?php 
 $h=q("SELECT ia.*, ap.status, ap.feedback FROM input_aspirasi ia LEFT JOIN aspirasi ap ON ia.id_pelaporan=ap.id_pelaporan WHERE ia.nis='$_SESSION[user]' ORDER BY ia.id_pelaporan DESC");
                    while($r=mysqli_fetch_assoc($h)){ ?>
                        <div class="border rounded p-3 mb-3 bg-white shadow-sm">
                            <div class="d-flex justify-content-between align-items-start">
                                <h5><b>Lokasi: <?= $r['lokasi'] ?></b></h5>
                                <span class="badge bg-secondary"><?= $r['waktu'] ?></span>
                            </div>
                            <p class="text-muted mt-2"><?= $r['ket'] ?></p>
                            <div class="mt-2 p-2 bg-light rounded border">
                                <strong>Status:</strong> 
                                <span class="badge bg-<?= (isset($r['status']) && $r['status']=='Selesai' ? 'success' : 'warning') ?>">
                                    <?= isset($r['status']) ? $r['status'] : 'Menunggu Antrian' ?>
                                </span><br>
                                <strong>Feedback:</strong> 
                                <span class="text-primary italic">
                                    <?= !empty($r['feedback']) ? $r['feedback'] : 'Admin belum memberikan tanggapan' ?>
                                </span>
                            </div>
                        </div>
                    <?php } ?>
                </div>
            <?php } ?>

        <?php } else { ?>
        
            <?php if($page=="user_admin"){ ?>
                <div class="card p-4">
                    <h3>Tambah Akun Admin Baru</h3>
                    <form method="post" class="row g-2 mb-4">
                        <div class="col-md-5"><input name="username" class="form-control" placeholder="Username" required></div>
                        <div class="col-md-5"><input name="password" class="form-control" placeholder="Password" required></div>
                        <div class="col-md-2"><button name="add_admin" class="btn btn-primary w-100">Tambah</button></div>
                    </form>
                    <table class="table table-striped align-middle">
                        <thead class="table-light">
                        <tr><th>Username</th>
                        <th>Password (Edit)</th>
                        <th class="text-center">Aksi</th>
                        </tr></thead>
                        <tbody>
                            <?php $ad=q("SELECT * FROM admin"); while($r=mysqli_fetch_assoc($ad)): ?>
                                <tr>
                                    <td><?= $r['username'] ?></td>
                                    <td>
                                        <form method="post" class="input-group input-group-sm">
                                            <input type="hidden" name="id_admin" value="<?= $r['id_admin'] ?>">
                                            <input name="password" class="form-control" value="<?= $r['password'] ?>">
                                            <button name="edit_admin" class="btn btn-warning">Simpan</button>
                                        </form>
                                    </td>
         <td class="text-center">
             <a href="?page=user_admin&del_admin=<?= $r['id_admin'] ?>" class="btn btn-danger btn-sm" onclick="return confirm('Hapus admin?')">Hapus</a>
                                    </td>
                                </tr>
                            <?php endwhile; ?>
                        </tbody>
                    </table>
                </div>
            <?php } ?>

            <?php if($page=="kategori"){ ?>
                <div class="card p-4 shadow-sm">
                    <h3>Data Kategori Fasilitas</h3>
                    <form method="post" class="input-group mb-3">
                        <input name="nama" class="form-control" placeholder="Kategori Baru...">
                        <button name="add_kat" class="btn btn-primary px-4">Tambah</button>
                    </form>
                    <table class="table border">
                        <thead class="table-light"><tr><th>Nama Kategori</th><th>Tindakan</th></tr></thead>
                        <?php $k=q("SELECT * FROM kategori"); while($r=mysqli_fetch_assoc($k)): ?>
                            <tr>
      <td><?= $r['ket_kategori'] ?></td>
  <td><a href="?page=kategori&del_kat=<?= $r['id_kategori'] ?>" class="btn btn-outline-danger btn-sm">Hapus</a></td>
                            </tr>
                        <?php endwhile; ?>
                    </table>
                </div>
            <?php } ?>

            <?php if($page=="siswa"){ ?>
                <div class="card p-4">
                    <h3>Master Data Siswa</h3>
                    <form method="post" class="row g-2 mb-4">
                        <div class="col-md-5"><input name="nis" class="form-control" placeholder="NIS" required></div>
                        <div class="col-md-5"><input name="kelas" class="form-control" placeholder="Kelas" required></div>
                        <div class="col-md-2"><button name="register" class="btn btn-primary w-100">Tambah</button></div>
                    </form>
                    <table class="table table-hover border align-middle">
                        <thead class="table-light">
                            <tr><th>NIS (Login)</th><th>Kelas (Pass)</th><th class="text-center">Aksi</th></tr>
                        </thead>
                        <tbody>
                            <?php $s=q("SELECT * FROM siswa ORDER BY nis ASC"); while($r=mysqli_fetch_assoc($s)): ?>
                                <tr>
                                    <td><b><?= $r['nis'] ?></b></td>
                                    <td>
                                        <form method="post" class="input-group input-group-sm">
                                            <input type="hidden" name="nis" value="<?= $r['nis'] ?>">
                                            <input name="kelas" class="form-control" value="<?= $r['kelas'] ?>">
                                            <button name="edit_siswa" class="btn btn-warning">Update</button>
                                        </form>
                                    </td>
                                    <td class="text-center">
                                        <a href="?page=siswa&del_siswa=<?= $r['nis'] ?>" class="btn btn-danger btn-sm">Hapus</a>
                                    </td>
                                </tr>
                            <?php endwhile; ?>
                        </tbody>
                    </table>
                </div>
            <?php } ?>

            <?php if($page=="aspirasi"){ ?>
                <div class="card p-4 mb-4 bg-light shadow-sm">
                    <h5>Cari Laporan</h5>
                    <form method="get" class="row g-2 text-center">
                        <input type="hidden" name="page" value="aspirasi">
                        <div class="col-md-4">
                            <input type="date" name="tgl" class="form-control" value="<?= @$_GET['tgl'] ?>">
                        </div>
                        <div class="col-md-4">
                            <select name="kat_cari" class="form-select">
                                <option value="">Semua Kategori</option>
                                <?php 
                                $kc=q("SELECT * FROM kategori"); 
                                while($rk=mysqli_fetch_assoc($kc)) 
                                echo "<option value='$rk[id_kategori]' ".(@$_GET['kat_cari']==$rk['id_kategori']?'selected':'').">$rk[ket_kategori]</option>"; 
                                ?>
                            </select>
                        </div>
                        <div class="col-md-4">
                            <button type="submit" class="btn btn-primary w-100">Filter Sekarang</button>
                        </div>
                    </form>
                </div>

                <div class="card p-4 shadow-sm">
                    <h3>Daftar Pengaduan Masuk</h3>
                    <div class="table-responsive mt-3">
                        <table class="table table-bordered table-sm align-middle">
                            <thead class="table-light">
                                <tr>
                                    <th>Tgl/NIS</th>
                                    <th>Isi Pengaduan</th>
                                    <th style="width:35%">Tanggapan & Status</th>
                                </tr>
                            </thead>
                            <tbody>
                                <?php
                                $where = " WHERE 1=1 ";
                                if(!empty($_GET['tgl'])) $where .= " AND DATE(ia.waktu) = '$_GET[tgl]' ";
                                if(!empty($_GET['kat_cari'])) $where .= " AND ia.id_kategori = '$_GET[kat_cari]' ";
                                                              
                                $h_admin = q("SELECT ia.*, ap.status, ap.feedback 
                                              FROM input_aspirasi ia 
                                              LEFT JOIN aspirasi ap ON ia.id_pelaporan=ap.id_pelaporan 
                                              $where ORDER BY ia.id_pelaporan DESC");
                                              
                                while($rh = mysqli_fetch_assoc($h_admin)){ ?>
     <tr>
        <td><small class="badge bg-secondary"><?= $rh['waktu'] ?></small><br><b>NIS: <?= $rh['nis'] ?></b></td>
          <td><span class="text-primary fs-6 fw-bold">[<?= $rh['lokasi'] ?>]</span><br><?= $rh['ket'] ?></td>
              <td>
           <form method="post" class="bg-light p-2 rounded">
         <input type="hidden" name="id_pelaporan" value="<?= $rh['id_pelaporan'] ?>">
   <input name="feedback" class="form-control form-control-sm mb-1" value="<?= $rh['feedback'] ?>" placeholder="Balas feedback...">
         <div class="input-group">
             <select name="status" class="form-select form-select-sm">
                  <option value="Menunggu" <?= ($rh['status']=='Menunggu' || is_null($rh['status']))?'selected':'' ?>>Menunggu</option>
                     <option value="Proses" <?= ($rh['status']=='Proses')?'selected':'' ?>>Proses</option>
                        <option value="Selesai" <?= ($rh['status']=='Selesai')?'selected':'' ?>>Selesai</option>
                    </select>
               <button name="proses" class="btn btn-sm btn-primary">Update</button>
             </div>
          </form>
                                        </td>
                                    </tr>
                                <?php } ?>
                            </tbody>
                        </table>
                    </div>
                </div>
            <?php } ?>
        <?php } ?>
    <?php } ?>
</div>

<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.0/dist/js/bootstrap.bundle.min.js"></script>
</body>
</html>