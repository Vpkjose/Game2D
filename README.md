# Game2D
  2D platform style video game in development in unity
  
first character movement script and animation:
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class playercontroller : MonoBehaviour
{
    // Start is called before the first frame update
    [Header ("Movimiento")]
    public float moveSpeed;

     [Header ("Salto")]
     public float jumpForce;
    [Header ("Componentes")]
    public Rigidbody2D theRB;
    [Header ("Animator")]
    private Animator anim;
    void Start()
    {
       anim = GetComponent<Animator>(); 
    }

    // Update is called once per frame
    void Update()
    {
         theRB.velocity = new Vector2(moveSpeed*Input.GetAxisRaw("Horizontal"),theRB.velocity.y);

         if(Input.GetButtonDown("Jump"))
         {
             theRB.velocity = new Vector2(theRB.velocity.x, jumpForce);
         }
         anim.SetFloat("moveSpeed",Mathf.Abs(theRB.velocity.x));
    }
}

