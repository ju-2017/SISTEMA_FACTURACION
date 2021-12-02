# SISTEMA_FACTURACION

Listar categoria

            Lib_TCategoria objC = new Lib_TCategoria();

            if (!objC.listarCategoria(DgvDatosC))
            {
                MessageBox.Show(objC.Error);
                return;
            }
            
            
PRODUCTO--------------------------------------------------

        private void BtnInsertar_Click(object sender, EventArgs e)
        {
            Lib_TProducto objP = new Lib_TProducto();

            try
            {
                objP.Nombre1 = TxtNombre.Text;
                objP.Id_producto = TxtProducto.Text;
                objP.Precio_actual = Convert.ToDouble(TxtPrecio_Actual.Text);

                if (objP.grabarProducto())
                {
                    MessageBox.Show("Se Inserto el registro correctamente");
                    return;
                }
                else
                {
                    MessageBox.Show(objP.Error);
                    return;
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
                return;
            }


        }

        private void BtnActualizar_Click(object sender, EventArgs e)
        {

            Lib_TProducto objP = new Lib_TProducto();

            try
            {
                objP.Nombre1 = TxtNombre.Text;
                objP.Id_producto = TxtProducto.Text;
                objP.Precio_actual = Convert.ToDouble(TxtPrecio_Actual.Text);

                if (objP.actualizarProducto())
                {
                    MessageBox.Show("Se actualizo el registro correctamente");
                    return;
                }
                else
                {
                    MessageBox.Show(objP.Error);
                    return;
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
                return;
            }

        }

        private void BtnEliminar_Click(object sender, EventArgs e)
        {
            Lib_TProducto objP = new Lib_TProducto();

            try
            {

                objP.Id_producto = TxtProducto.Text;
    

                if (objP.eliminarEmpleado())
                {
                    MessageBox.Show("Se elimino el registro correctamente");
                    return;
                }
                else
                {
                    MessageBox.Show(objP.Error);
                    return;
                }

            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
                return;
            }
        }

        private void BtnConsultar_Click(object sender, EventArgs e)
        {
            Lib_TProducto objP = new Lib_TProducto();

            try
            {
                objP.Id_producto = TxtProducto.Text;

                if (!objP.consultarProducto())
                {
                    MessageBox.Show(objP.Error);
                    return;
                }
                else
                {
                    if (objP.Objraider.HasRows)
                    {
                        objP.Objraider.Read();
                        TxtNombre.Text = objP.Objraider.GetString(1);
                        TxtPrecio_Actual.Text = objP.Objraider.GetString(2);
                        objP.Objraider.Close();
                    }
                }
            }
            catch (Exception ex)
            {
                MessageBox.Show(ex.Message);
                return;
            }
        }

        private void BtnListar_Click(object sender, EventArgs e)
        {
            Lib_TProducto objP = new Lib_TProducto();

            if (!objP.listarProducto(DgvDatosP))
            {
                MessageBox.Show(objP.Error);
                return;
            }
        }
    }
}



COMBO BOX 

        private void llenarComboCategoria()
        {

            Lib_TProducto objP = new Lib_TProducto();
            if (!objP.comboCategoria(comboCategoria))
            {
                MessageBox.Show(objP.Error);
                return;
            }


        }

        private void BtnIdCategoria_Click(object sender, EventArgs e)
        {
            TxtProducto.Text = comboCategoria.SelectedValue.ToString();
            return;

        }
