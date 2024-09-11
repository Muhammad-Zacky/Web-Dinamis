                    <?php
                    if (isset($_POST['simpan'])) {
                        $nama = htmlspecialchars($_POST['nama']);
                        $nim = htmlspecialchars($_POST['nim']);
                        $nilai = htmlspecialchars($_POST['nilai']);
                        $jurusan = htmlspecialchars($_POST['jurusan']);
                        $tanggal_lahir = htmlspecialchars($_POST['tanggal_lahir']);
                        $jk = htmlspecialchars($_POST['jk']);
                        $alamat = htmlspecialchars($_POST['alamat']);
                        $hobiArray = $_POST['hobi'] ?? [];
                        $hobi = implode(', ', $hobiArray);

                        // Konek ke database
                        $conn = new mysqli("localhost", "root", "", "mi2b");


                        // Koneksi 
                        if ($conn->connect_error) {
                            die("Koneksi gagal: " . $conn->connect_error);
                        }

                        // Masukan data ke database
                        $sql = "INSERT INTO mahasiswa (nama, nim, nilai, jurusan, tanggal_lahir, jk, hobi, alamat) 
                                VALUES ('$nama', '$nim', '$nilai', '$jurusan', '$tanggal_lahir', '$jk', '$hobi', '$alamat')";

                        if ($conn->query($sql) === TRUE) {
                            echo "<div class='mt-4 p-3 bg-success text-white border rounded'>Data mahasiswa berhasil disimpan</div>";
                        } else {
                            echo "<div class='mt-4 p-3 bg-danger text-white border rounded'>Error: " . $sql . "<br>" . $conn->error . "</div>";
                        }

                        $conn->close();
                    }
                    ?>
