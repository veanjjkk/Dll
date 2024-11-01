private async void timer1_Tick(object sender, EventArgs e)
        {
            timer1.Stop();
            await Task.Delay(1000); // milliseconds 
            WebClient updatecheck = new WebClient();

            //updating loader bar
            panel3.Width = 40;
            await Task.Delay(400);
            panel3.Width = 80;
            await Task.Delay(400);
                      
            if (!updatecheck.DownloadString("https://raw.githubusercontent.com/veanjjkk/1.1/refs/heads/main/UpdateCheck").Contains("1.1"))
            {
                label2.Text = ("Checking For Update");
                await Task.Delay(1000);
                MessageBox.Show("You Do Not Have The Correct Version For Mirus Exploit.", "Mirus");
                await Task.Delay(1000); //milliseconds 
                Application.Exit();
            }
            else
            {
                panel3.Width = 120;
                await Task.Delay(400);
                panel3.Width = 160;                
                label2.Text = ("Checking For Patch");
                await Task.Delay(2000);
                WebClient patchcheck = new WebClient();
                if (!patchcheck.DownloadString("https://raw.githubusercontent.com/veanjjkk/1.1/refs/heads/main/PatchCheck").Contains("notpatched"))
                {
                    label2.Text = ("Mirus Is Patched Right Now.");                   
                    MessageBox.Show("Patched.", "Mirus");
                    await Task.Delay(1000); //milliseconds 
                    Application.Exit();
                }
                else
                {
                    await Task.Delay(500);
                    panel3.Width = 200;                   
                    await Task.Delay(400);
                    panel3.Width = 240;
                    await Task.Delay(400);
                    panel3.Width = 280;
                    await Task.Delay(400);
                    panel3.Width = 320;
                    await Task.Delay(400);
                    panel3.Width = 350;
                    label2.Text = ("Loading Mirus Exploit");
                    await Task.Delay(1000);
                    this.Hide(); // hides loader ui
                    MainUI mainui = new MainUI(); 
                    mainui.Show(); //shows new ui:)

                }               
            }
        }
